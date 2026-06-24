#  Class 11 Transfer Student Admission Portal

A responsive, user-friendly web application designed for Horizon Academy to streamline Class XI admission process specifically for transfer students. Built with HTML, CSS, and JavaScript.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

---

##  Overview

This project provides a complete admission portal interface for **Horizon Academy's Class XI transfer admissions (2026-27 session)**. It's designed to collect all necessary information from students transferring from other schools, including previous academic records, transfer certificates, and stream preferences.

### Key Highlights:
-  Fully responsive design (mobile, tablet, desktop)
-  Modern UI with gradient backgrounds and smooth shadows
-  Client-side form validation
-  File upload for Transfer Certificate
-  Informative sidebar with requirements and deadlines
-  User-friendly error handling

---

##  Features

### Core Functionality
- **Transfer-Specific Form Fields**
  - Previous school details
  - Board selection (CBSE, ICSE, IB, State Board)
  - Class X percentage/CGPA input
  - Transfer Certificate upload (PDF/JPG support)
  - Reason for transfer

- **Smart Validation**
  - Real-time input validation
  - Indian mobile number format check (+91)
  - Email format verification
  - File type and size validation
  - Required field indicators

- **User Experience**
  - Sticky navigation header
  - Progress indicators
  - Success confirmation alert
  - Auto-reset after submission
  - Loading state feedback

### Visual Design
- Professional academic color scheme (navy blue + orange accents)
- Font Awesome 6 icons integration
- Smooth hover animations
- Card-based layout with subtle shadows
- Responsive grid system
- Accessible form labels

---
<img width="1888" height="8143" alt="image" src="https://github.com/user-attachments/assets/0e1c8c00-cb78-474c-bb26-98e68225fe11" />


### Mobile View
```
┌───────────────────┐
│  Horizon Academy  │
│  Transfer 2026    │
├───────────────────┤
│  Transfer Form    │
│ Student Name:     │
│ [_____________]   │
│ Previous School:  │
│ [_____________]   │
│ Stream: [Science▼]│
│  Upload TC:       │
│ [Choose File]     │
│ [ Submit]         │
├───────────────────┤
│  Requirements     │
│  TC Original      │
│  Mark Sheet       │
├───────────────────┤
│  Helpline         │
│  +91 11 4235 6789 │
└───────────────────┘
```

---

## Installation

### Method 1: Direct Download
1. Download the ZIP file from this repository
2. Extract the contents
3. Open `index.html` in any modern browser

### Method 2: Git Clone
```bash
git clone https://github.com/yourusername/class-11-transfer-admission.git
cd class-11-transfer-admission
# Open index.html in your browser
```

### Method 3: GitHub Pages Deployment
1. Fork this repository
2. Go to Settings → Pages
3. Select `main` branch as source
4. Save - your site will be live at `https://yourusername.github.io/class-11-transfer-admission/`

---

## Usage

### For Students/Parents:
1. Open the website in any browser
2. Fill in all required fields:
   - Personal details (name, DOB, gender)
   - Previous school information
   - Academic records (board, percentage)
   - Preferred stream for Class XI
   - Contact information
   - Upload Transfer Certificate (PDF/JPG)
   - Provide reason for transfer
3. Click "Submit Transfer Application"
4. Receive confirmation message with next steps

### For Administrators:
- All form submissions are logged to browser console (demo mode)
- In production, modify the `handleSubmit()` function to send data to your backend server
- Update deadlines and contact information in the HTML
- Customize validation rules as needed

---

## Project Structure

```
class-11-transfer-admission/
│
├── index.html              # Main admission portal
├── README.md               # Project documentation
│
├── assets/                 # (Optional) Static assets
│   ├── css/
│   │   └── style.css       # External stylesheet (currently inline)
│   ├── js/
│   │   └── script.js       # External JavaScript (currently inline)
│   └── images/
│       └── logo.png        # School logo
│
└── .gitignore              # Git ignore file
```

---

## 📝 Form Fields

### Student Information
| Field | Type | Required | Description |
|-------|------|----------|-------------|
| Student Full Name | text | ✅ | As per previous school records |
| Date of Birth | date | ✅ | Student's date of birth |
| Gender | select | ✅ | Male/Female/Other |
| Previous School | text | ✅ | Name of last school attended |
| Board | select | ✅ | CBSE/ICSE/IB/State Board/Other |
| Percentage/CGPA | text | ✅ | Class X academic performance |
| Preferred Stream | select | ✅ | Science/Commerce/Arts |
| Parent Mobile | tel | ✅ | 10-digit Indian mobile number |
| Email | email | ✅ | Parent/guardian email |
| Address | textarea | ✅ | Current residential address |
| Transfer Certificate | file | ✅ | PDF/JPG upload |
| Reason for Transfer | textarea | ✅ | Brief explanation |

---

## ✅ Validation Rules

### Client-Side Validation:
```javascript
// Mobile number validation
/^[6-9]\d{9}$/  // Indian mobile format

// Email validation
/^\S+@\S+\.\S+$/  // Basic email format

// Required fields check
All fields marked with * must be filled

// File validation
- File must be selected (TC upload)
- Supported formats: PDF, JPG, JPEG, PNG
- Max size: Configure in script (default: unrestricted for demo)
```

### Custom Error Messages:
- "Please fill all required fields."
- "Please enter a valid 10-digit Indian mobile number."
- "Please enter a valid email address."
- "Please upload the Transfer Certificate."

---

## 🎨 Customization

### Changing School Details
Edit the header section in `index.html`:
```html
<div class="school-name">
  <h1>Your School Name</h1>
  <p>Your Tagline</p>
</div>
```

### Updating Colors
Modify CSS variables in the `<style>` section:
```css
/* Main theme colors */
header { background: linear-gradient(135deg, #0b2b4f 0%, #1a4b7a 100%); }
.btn { background: #f9844a; }  /* Orange accent */
```

### Adding New Streams
Add options to the stream select:
```html
<select id="stream">
  <option value="Science">Science (PCM/PCB)</option>
  <option value="Commerce">Commerce</option>
  <option value="Arts">Arts / Humanities</option>
  <!-- Add more options -->
</select>
```

### Integrating Backend
Replace the `handleSubmit()` function:
```javascript
async function handleSubmit(event) {
  event.preventDefault();
  const formData = new FormData(document.getElementById('admissionForm'));
  
  try {
    const response = await fetch('/api/admissions', {
      method: 'POST',
      body: formData
    });
    // Handle response
  } catch (error) {
    console.error('Submission failed:', error);
  }
}
```

---

## 🌐 Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | ✅ Fully Supported |
| Firefox | 88+ | ✅ Fully Supported |
| Safari | 14+ | ✅ Fully Supported |
| Edge | 90+ | ✅ Fully Supported |
| Opera | 76+ | ✅ Fully Supported |
| Internet Explorer | 11 | ⚠️ Partial Support |

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** changes: `git commit -m 'Add amazing feature'`
4. **Push** to branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

### Contribution Ideas:
- Add multi-language support
- Implement CAPTCHA for spam prevention
- Create admin dashboard
- Add payment gateway integration
- Email notification system
- Database integration (MySQL/MongoDB)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2026 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software...
```
