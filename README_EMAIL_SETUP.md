# Contact Form Email Setup Guide

Your portfolio now includes a functional contact form! Here are the steps to make it work:

## Option 1: Using Formspree (Recommended - Easy Setup)

1. **Sign up at Formspree:**
   - Go to https://formspree.io/
   - Create a free account
   - Create a new form
   - You'll get a form endpoint like: `https://formspree.io/f/YOUR_FORM_ID`

2. **Update your HTML:**
   - In `portfolio.html`, find the line with `YOUR_FORM_ID`
   - Replace `YOUR_FORM_ID` with your actual Formspree form ID
   - The line should look like: `const response = await fetch('https://formspree.io/f/xrgwpzbl', {`

3. **Configure Formspree:**
   - In your Formspree dashboard, set up email notifications to `faisal.offl123@gmail.com`
   - Enable reCAPTCHA if desired
   - Customize the thank you page (optional)

## Option 2: Using EmailJS (More Features)

1. **Sign up at EmailJS:**
   - Go to https://www.emailjs.com/
   - Create a free account
   - Create an email service (Gmail, Outlook, etc.)
   - Create an email template

2. **Get your credentials:**
   - User ID (Public Key)
   - Service ID
   - Template ID

3. **Update the JavaScript:**
   - Replace `YOUR_EMAILJS_USER_ID` with your actual User ID
   - Replace `YOUR_SERVICE_ID` with your actual Service ID
   - Replace `YOUR_TEMPLATE_ID` with your actual Template ID

4. **Email Template Variables:**
   - `{{from_name}}` - Visitor's name
   - `{{from_mobile}}` - Visitor's mobile number
   - `{{message}}` - Visitor's message
   - `{{to_email}}` - Your email (faisal.offl123@gmail.com)

## Option 3: Simple PHP Backend (If you have a web server)

Create a file called `send_email.php`:

```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST['name'];
    $mobile = $_POST['mobile'];
    $message = $_POST['message'];
    
    $to = "faisal.offl123@gmail.com";
    $subject = "Contact Form Submission from " . $name;
    
    $email_body = "Name: " . $name . "\n";
    $email_body .= "Mobile: " . $mobile . "\n";
    $email_body .= "Message: " . $message . "\n";
    
    $headers = "From: noreply@yourdomain.com";
    
    if (mail($to, $subject, $email_body, $headers)) {
        echo json_encode(["success" => true]);
    } else {
        echo json_encode(["success" => false]);
    }
}
?>
```

Then update the fetch URL in your HTML to point to this PHP file.

## Testing Your Form

1. Open your `portfolio.html` file in a web browser
2. Navigate to the "Let's Connect" section
3. Fill out the form with test data
4. Submit and check if you receive the email

## Current Form Features

✅ **Name field** - Required text input
✅ **Mobile number field** - Required telephone input
✅ **Message field** - Required textarea
✅ **Form validation** - All fields are required
✅ **Loading states** - Button shows "Sending..." during submission
✅ **Success/Error messages** - User feedback after submission
✅ **Responsive design** - Works on all devices
✅ **Theme integration** - Matches your portfolio's dark/light theme

## Troubleshooting

- **Form not sending emails:** Check your Formspree/EmailJS configuration
- **CORS errors:** Make sure you're testing on a proper web server, not file://
- **Styling issues:** The form inherits your portfolio's theme variables

## Next Steps

1. Choose one of the email services above
2. Follow the setup instructions
3. Test the form thoroughly
4. Consider adding reCAPTCHA for spam protection

Your contact form is now ready to collect visitor information and send it directly to `faisal.offl123@gmail.com`!