# Image Migration Guide

This guide provides instructions for managing and migrating images used in the Introduction to Secret Scanning Skills repository.

## Overview

This repository uses images to enhance the learning experience by providing visual guidance for users completing the secret scanning exercises. All images are currently hosted using GitHub's user-attachments service, which provides reliable CDN-backed hosting for documentation assets.

## Current Image Hosting

### GitHub User Attachments

Images in this repository are hosted on GitHub's user-attachments service:
- **Format**: `https://github.com/user-attachments/assets/{unique-id}`
- **Used in**: Step documentation files (`.github/steps/*.md`)
- **Benefits**: 
  - Integrated with GitHub's infrastructure
  - CDN-backed for fast loading
  - Reliable availability
  - No repository bloat from binary files

### Image Inventory

The repository currently uses images in the following locations:

#### Step 1: Enable Secret Scanning (`1-enable-secret-scanning.md`)
- Secret protection configuration settings
- New file button screenshots
- File content examples

#### Step 2: Review Alerts (`2-review-alerts.md`)
- Filtered alerts list views
- Alert detail page screenshots
- Alert closure workflow screenshots

#### Step 3: Enable Push Protection (`3-enable-push-protection.md`)
- Secret protection configuration with push protection enabled
- Edit file button
- Credentials file editing screenshot
- Push protection alert dialog
- Bypass push protection options

## Migration Scenarios

### Scenario 1: Migrating from Another Repository

If you're creating a similar Skills repository and want to reuse these images:

1. **Review existing images**: Examine the step files to understand which images are used
2. **Create new screenshots**: Take new screenshots in your own repository context
3. **Upload to GitHub**: 
   - Create an issue or comment in your repository
   - Drag and drop images into the comment box
   - Copy the generated markdown with the `user-attachments` URL
   - Use these URLs in your documentation files

### Scenario 2: Updating Existing Images

When images need to be updated (e.g., GitHub UI changes):

1. **Identify outdated images**: Review step files and note which images need updating
2. **Take new screenshots**: Capture updated screenshots showing current UI
3. **Upload new images**: Use GitHub's issue/PR comment interface to upload
4. **Update references**: Replace old URLs with new `user-attachments` URLs in markdown files
5. **Verify**: Check that all images render correctly in the GitHub UI

### Scenario 3: Migrating to Alternative Hosting

If you need to migrate away from user-attachments (e.g., for offline access):

1. **Download all images**:
   ```bash
   # Extract all image URLs
   grep -r "user-attachments/assets" .github/steps/*.md | \
     grep -oE 'https://[^)\"]+' | \
     sort -u > image-urls.txt
   
   # Download images
   mkdir -p .github/images
   while read url; do
     filename=$(echo $url | grep -oE '[a-f0-9-]{36}')
     curl -L "$url" -o ".github/images/${filename}.png"
   done < image-urls.txt
   ```

2. **Update references in markdown files**:
   ```bash
   # Replace user-attachments URLs with local paths
   # Example: Change to relative paths
   sed -i 's|https://github.com/user-attachments/assets/\([a-f0-9-]*\)|../.github/images/\1.png|g' .github/steps/*.md
   ```

3. **Commit image files**: Add the `.github/images` directory to version control
4. **Update `.gitignore` if needed**: Ensure image files are not excluded

### Scenario 4: Migrating to GitHub Releases

For better versioning and management:

1. **Create a new release**: Go to Releases → Draft a new release
2. **Upload images**: Attach all images to the release
3. **Get URLs**: Copy the direct URLs for each uploaded asset
4. **Update markdown files**: Replace user-attachments URLs with release asset URLs
5. **Tag release**: Tag appropriately (e.g., `assets-v1.0`)

## Best Practices

### Image Management

1. **Descriptive alt text**: Always provide meaningful alt text for accessibility
   ```markdown
   ![Secret protection configuration showing enabled status](url)
   ```

2. **Consistent sizing**: Use width attributes for consistent display
   ```markdown
   <img width="400" alt="Description" src="url" />
   ```

3. **Relative paths for local images**: If storing images in the repository
   ```markdown
   ![Alt text](../images/screenshot.png)
   ```

4. **Avoid private repositories**: Ensure images are accessible to all users

### Documentation Standards

1. **Keep images up-to-date**: Review images when GitHub UI changes
2. **Test all links**: Verify images render correctly before merging changes
3. **Use high-quality screenshots**: Ensure text is readable and UI is clear
4. **Crop appropriately**: Show only relevant UI elements
5. **Consider dark/light mode**: Provide context if screenshots vary by theme

## Validation

### Check for Broken Images

Run this command to extract and verify all image URLs:

```bash
# Extract all image URLs from markdown files
grep -rh 'src="http' .github/steps/*.md | \
  grep -oE 'https://[^"]+' | \
  sort -u | \
  while read url; do
    if curl -f -s -o /dev/null "$url"; then
      echo "✓ $url"
    else
      echo "✗ $url (broken)"
    fi
  done
```

### Render Check

1. Preview markdown files in GitHub web interface
2. Verify all images load correctly
3. Check that images are appropriately sized
4. Confirm alt text is descriptive

## Troubleshooting

### Images Not Displaying

**Problem**: Images show as broken links

**Solutions**:
- Verify the URL is correct and complete
- Check if the image URL is from a private repository
- Ensure the image was not deleted from user-attachments
- Try re-uploading the image and updating the URL

### Images Too Large/Small

**Problem**: Images don't display at the right size

**Solutions**:
- Add width attribute: `<img width="400" src="url" />`
- Use consistent sizing across similar screenshots
- Consider the GitHub markdown preview display width

### Slow Loading Images

**Problem**: Images take too long to load

**Solutions**:
- User-attachments uses CDN, so this is usually not an issue
- Check image file sizes (compress if over 1MB)
- Consider using WebP or optimized PNG formats
- Ensure images are hosted on reliable service

## Additional Resources

- [GitHub Markdown Guide](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [GitHub Skills Documentation](https://skills.github.com/)
- [Accessibility Guidelines for Images](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images)

## Maintenance

This guide should be updated when:
- New images are added to the repository
- Image hosting strategy changes
- GitHub's user-attachments service behavior changes
- Migration procedures are improved or updated

---

Last Updated: February 2026
