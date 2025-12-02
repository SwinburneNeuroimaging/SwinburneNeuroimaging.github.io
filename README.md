# SwinburneNeuroimaging.github.io
Swinburne Neuroimaging Documentation

This repo will contain all manuals, guides and other documents for the user community of Swinburne Neuroimaging.

## Table of Contents
- Getting Started
- Adding New Content
- Adding New Tabs
- Basic Markdown
- Commiting and Pushing to GitHub


### Getting Started
### Step 1: Clone the Repo
First, clone the repository to your local machine:
```
git clone https://github.com/SwinburneNeuroimaging/SwinburneNeuroimaging.github.io.git
cd SwinburneNeuroimaging.github.io
```
### Step 2: Checkout to the Developement Branch
```
git checkout wiki
```
### Step 3: Setup Python Environment
```
# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
.\venv\Scripts\activate

# Install MkDocs Material
pip install mkdocs-material
```
# Step 5: Serve documentation to preview changes locally
```
mkdocs serve --livereload
```
The site will be available at http://localhost:8000. The server will automatically reload when you save changes.

## Adding New Content
### Creating a New Page
1. Navigate to the `docs` directory
2. Create a new Markdown file with a descriptive name (e.g., mri_safety.md)
3. Add your content using Markdown syntax (see below for examples)
4. Save the file


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
```
    ```python
    def process_mri_data(filepath):
        """Process MRI data from file."""
        data = load_data(filepath)
        return preprocess(data)
    ```
```


With line numbers and highlighting:
```
    ```python linenums="1" hl_lines="2-3"
    def analyze_scan(scan_id):
        # Load the scan data
        data = load_scan(scan_id)
        return analyze(data)
    ```
```

### Images
```
![Alt text for image](images/scan-example.png)
```
Or with a caption
```
![MRI Scan Example](images/scan-example.png)
*Figure 1: Example MRI scan showing...*
```

### Admonitions (Callouts)

Types: `note`, `abstract`, `info`, `tip`, `success`, `question`, `warning`, `failure`, `danger`, `bug`, `example`, `quote`

```
!!! note "Important Information"
    This is a note callout with important information.

!!! warning "Safety Warning"
    Always check for metal objects before entering the scanner room.

!!! tip "Pro Tip"
    Use this shortcut to save time during data processing.

!!! danger "Critical Safety Alert"
    Never enter the scanner room with metal objects.
```
Collapsible Callouts:
```
??? abstract "Important Information"
    This is a note callout with important information.

??? info "Safety Warning"
    Always check for metal objects before entering the scanner room.

??? success "Pro Tip"
    Use this shortcut to save time during data processing.

??? question "Critical Safety Alert"
    Never enter the scanner room with metal objects.
```

### Diagrams (Mermaid)
MkDocs Material supports Mermaid diagrams

- Flowcharts:
```
    ```mermaid
    graph LR
    A[Start] --> B{Failure?};
    B -->|Yes| C[Investigate...];
    C --> D[Debug];
    D --> B;
    B ---->|No| E[Success!];
    ```
```

- Sequence Diagrams:
```
    ```mermaid
    sequenceDiagram
        participant R as Researcher
        participant P as Participant
        participant S as Scanner
    
        R->>P: Explain procedure
        P->>R: Sign consent form
        R->>S: Position participant
        S->>S: Run scanning protocol
        S->>R: Complete scan
    ```
```