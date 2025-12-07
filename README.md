# Nutrition Awareness Website

A static website focused on nutrition awareness for children and adolescents living below the poverty line.

## Project Overview

This website aims to educate and raise awareness about childhood nutrition and food insecurity. It includes information about nutrition, our mission, upcoming events, and contact information.

## Features

- Responsive design that works on all devices
- Smooth scrolling navigation
- Information about nutrition importance
- About Us section with mission and goals
- Events and initiatives showcase
- Contact information section

## Local Testing

To test the website locally:

1. Open `index.html` in your web browser
2. Or use a simple HTTP server:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (if you have http-server installed)
npx http-server

# Using PHP
php -S localhost:8000
```

Then visit `http://localhost:8000` in your browser.

## Deployment to AWS S3 + CloudFront

### Prerequisites
- AWS CLI installed and configured
- An AWS account with appropriate permissions

### Deployment Steps

1. **Create S3 Bucket**
```bash
aws s3 mb s3://your-nutrition-website-bucket
```

2. **Enable Static Website Hosting**
```bash
aws s3 website s3://your-nutrition-website-bucket --index-document index.html
```

3. **Upload Files**
```bash
aws s3 sync . s3://your-nutrition-website-bucket --exclude ".git/*" --exclude "README.md"
```

4. **Set Bucket Policy for Public Access**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::your-nutrition-website-bucket/*"
        }
    ]
}
```

5. **Create CloudFront Distribution**
- Origin: Your S3 bucket website endpoint
- Default Root Object: index.html
- Enable HTTPS

## File Structure

```
sc-website/
├── index.html      # Main HTML file
├── styles.css      # Stylesheet
├── script.js       # JavaScript for interactions
└── README.md       # This file
```

## Customization

Feel free to customize:
- Contact information in `index.html`
- Colors in `styles.css` (main color: #2c5f2d, accent: #97c93d)
- Event details and descriptions
- Add images to enhance visual appeal

## Technologies Used

- HTML5
- CSS3 (with Grid and Flexbox)
- Vanilla JavaScript
- No external dependencies

## License

This project is for educational purposes.
