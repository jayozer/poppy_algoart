# Poppy Garden

Algorithmic art generator for Poppy Kids Pediatric Dentistry. Kids enter their name to create a unique, personalized poppy field landscape they can email home.

## Features

- **Name-based generation** - Each name creates a unique garden
- **Interactive controls** - Adjust sun, butterflies, clouds, mountains, water, rocks
- **Customizable poppies** - Change density, waviness, wind sway
- **Email to parents** - Send artwork directly via email
- **Fun "Surprise Me!"** - Generates random fun names like Daisy, Sparkle, Bubbles

## Usage

1. Open `poppy-landscape.html` in a browser
2. Enter your name and click "Create My Garden!"
3. Toggle elements and adjust sliders to customize
4. Enter parent's email and click "Send My Picture!"

## EmailJS Setup

The app uses [EmailJS](https://www.emailjs.com/) to send artwork to parents.

Configuration is in the HTML file (lines ~1097-1099):
```javascript
const EMAILJS_PUBLIC_KEY = "your_public_key";
const EMAILJS_SERVICE_ID = "your_service_id";
const EMAILJS_TEMPLATE_ID = "your_template_id";
```

Template variables:
- `{{to_email}}` - Parent's email address
- `{{child_name}}` - Child's name
- `{{image_data}}` - Base64 PNG image

## Tech

- p5.js for canvas rendering
- EmailJS for email delivery
- Single HTML file, no build required
