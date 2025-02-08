from pdf2image import convert_from_path

# Convert PDF pages to images
pdf_path = "/mnt/data/XSalesfy (1).pdf"
images = convert_from_path(pdf_path, dpi=150)

# Save images for web use
image_paths = []
for i, image in enumerate(images):
    img_path = f"/mnt/data/page_{i + 1}.png"
    image.save(img_path, "PNG")
    image_paths.append(img_path)

# Generate HTML content
html_content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XSalesfy Profile</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            text-align: center;
            background-color: #f4f4f4;
        }
        .container {
            width: 80%;
            margin: 20px auto;
            background: white;
            padding: 20px;
            box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
        }
        img {
            width: 100%;
            max-width: 800px;
            margin-bottom: 20px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>XSalesfy Profile</h1>
"""

# Add images to HTML
for img_path in image_paths:
    html_content += f'        <img src="{img_path}" alt="Page Image">\n'

html_content += """
    </div>
</body>
</html>
"""

# Save HTML file
html_path = "/mnt/data/index.html"
with open(html_path, "w") as file:
    file.write(html_content)

# Provide the HTML file to the user
html_path
