# Poppy Garden

Algorithmic art generator for **Poppy Kids Pediatric Dentistry**. Kids enter their name to create a unique, personalized poppy field landscape that can be emailed to parents.

## Features

- **Name-based generation** - Each name creates a unique garden
- **Interactive controls** - Toggle sun, butterflies, clouds, mountains, water, rocks
- **Customizable poppies** - Adjust density, waviness, wind sway
- **Fun "Surprise Me!"** - Generates random fun names (Daisy, Sparkle, Bubbles, etc.)
- **Email to parents** - Uploads artwork to cloud, emails download link
- **Download button** - Save full-size PNG directly

## Usage

1. Open `poppy-landscape.html` in a browser
2. Enter child's name and click "Create My Garden!"
3. Toggle elements and adjust sliders to customize
4. Click "Download Picture" to save locally, OR
5. Enter parent's email and click "Send Picture to Parent"

---

## Setup Guide

### 1. EmailJS Setup

[EmailJS](https://www.emailjs.com/) sends the email to parents.

1. Create account at emailjs.com
2. Add an email service (Gmail, etc.)
3. Create template with ID: `poppy_garden_art`
4. Update credentials in HTML (~lines 1109-1111):

```javascript
const EMAILJS_PUBLIC_KEY = "your_public_key";
const EMAILJS_SERVICE_ID = "your_service_id";
const EMAILJS_TEMPLATE_ID = "poppy_garden_art";
```

### 2. Cloudinary Setup

[Cloudinary](https://cloudinary.com/) hosts the artwork images.

1. Create free account at cloudinary.com
2. Get your **Cloud Name** from Dashboard
3. Create an **Upload Preset**:
   - Settings → Upload → Add upload preset
   - Set Signing Mode to **Unsigned**
   - Name it `poppy_art`
4. Update credentials in HTML (~lines 1114-1115):

```javascript
const CLOUDINARY_CLOUD_NAME = "your_cloud_name";
const CLOUDINARY_UPLOAD_PRESET = "poppy_art";
```

### 3. Email Template

In EmailJS, create/update template `poppy_garden_art`:

**Subject:**
```
{{child_name}}'s Poppy Garden from Poppy Kids!
```

**Body (HTML):**
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body { font-family: 'Segoe UI', Arial, sans-serif; background: #faf9f5; margin: 0; padding: 20px; }
    .container { max-width: 600px; margin: 0 auto; background: white; border-radius: 16px; overflow: hidden; box-shadow: 0 4px 20px rgba(0,0,0,0.1); }
    .header { background: linear-gradient(135deg, #F7931E, #ffb347); padding: 25px; text-align: center; }
    .header h1 { color: white; margin: 0; font-size: 24px; }
    .content { padding: 30px; text-align: center; }
    .name { color: #F7931E; font-weight: bold; font-size: 22px; }
    .message { color: #333; font-size: 16px; line-height: 1.6; margin: 15px 0; }
    .preview { max-width: 100%; border-radius: 8px; margin: 20px 0; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }
    .download-btn { display: inline-block; background: #F7931E; color: white; padding: 14px 30px; border-radius: 8px; text-decoration: none; font-weight: bold; font-size: 16px; margin: 10px 0; }
    .footer { background: #f5f3ee; padding: 25px; text-align: center; }
    .footer-title { color: #333; font-weight: bold; font-size: 16px; margin-bottom: 10px; }
    .footer-tagline { color: #F7931E; font-style: italic; margin-bottom: 15px; }
    .contact-info { color: #555; font-size: 14px; line-height: 1.8; margin-bottom: 15px; }
    .contact-info a { color: #F7931E; text-decoration: none; }
    .book-btn { display: inline-block; background: #F7931E; color: white; padding: 12px 25px; border-radius: 8px; text-decoration: none; font-weight: bold; font-size: 14px; }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1>Look What I Made!</h1>
    </div>
    <div class="content">
      <p class="name">{{child_name}}</p>
      <p class="message">created this poppy garden during their visit!</p>
      <img src="{{image_url}}" alt="{{child_name}}'s Poppy Garden" class="preview">
      <br>
      <a href="{{image_url}}" download class="download-btn">Download Artwork</a>
    </div>
    <div class="footer">
      <div class="footer-title">Poppy Kids Pediatric Dentistry</div>
      <div class="footer-tagline">Growing healthy smiles, one visit at a time!</div>
      <div class="contact-info">
        <a href="mailto:info@poppykidsdental.com">info@poppykidsdental.com</a><br>
        <a href="tel:+14154085775">(415) 408-5775</a>
      </div>
      <a href="https://dental4.me/poppykids/1" class="book-btn">Book an Appointment</a>
    </div>
  </div>
</body>
</html>
```

**Template Variables:**
- `{{to_email}}` - Parent's email (set in "To Email" field)
- `{{child_name}}` - Child's name
- `{{image_url}}` - Cloudinary image URL

---

## Tech Stack

- **p5.js** - Canvas rendering
- **EmailJS** - Email delivery
- **Cloudinary** - Image hosting
- Single HTML file, no build required

---

## Contact

**Poppy Kids Pediatric Dentistry**
Email: info@poppykidsdental.com
Phone: (415) 408-5775
Book: https://dental4.me/poppykids/1
