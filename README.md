# SwinburneNeuroimaging.github.io
Swinburne Neuroimaging Documentation

This repo will contain all manuals, guides and other documents for the user community of Swinburne Neuroimaging.

## Basic Markdown
### Text Formatting
```
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*
~~Strikethrough~~

- Bullet point 1
- Bullet point 2

1. Numbered item 1
2. Numbered item 2

[Link text](https://example.com)
```

### Code Blocks
Inline code: `code here`

Code blocks with syntax highlighting:

````python
def process_mri_data(filepath):
    """Process MRI data from file."""
    data = load_data(filepath)
    return preprocess(data)
````


With line numbers and highlighting:

````python linenums="1" hl_lines="2-3"
def analyze_scan(scan_id):
    # Load the scan data
    data = load_scan(scan_id)
    return analyze(data)
````


### Images
![Alt text for image](images/scan-example.png)

# Or with a caption
![MRI Scan Example](images/scan-example.png)
*Figure 1: Example MRI scan showing...*