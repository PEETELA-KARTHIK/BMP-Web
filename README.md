This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

Your contact form is now set up to send emails in real time when hosted:

- A new API route (`app/api/contact/route.ts`) has been created using Next.js API routes and Nodemailer.
- When a user submits the "Get in Touch" form, you will receive an email with their details.
- The email sending uses environment variables for SMTP configuration and the recipient address, so you can use any SMTP provider (like Gmail, Outlook, or a custom domain).

**What you need to do before deploying:**
1. Add the following environment variables to your `.env.local` file (or your hosting provider's environment settings):

```
SMTP_HOST=smtp.yourprovider.com
SMTP_PORT=465
SMTP_SECURE=true
SMTP_USER=your@email.com
SMTP_PASS=your_email_password
SMTP_FROM=your@email.com
CONTACT_RECEIVER_EMAIL=your@email.com
```
- Adjust the values to match your SMTP provider and the email address where you want to receive messages.

2. Run `npm install` to install the new `nodemailer` dependency.

3. Deploy your site. The contact form will work both locally and in production as long as the environment variables are set.

Let me know if you want help with a specific SMTP provider or want to test locally!

# Email Contact Form Setup

To enable the contact form to send emails, add the following environment variables to your `.env.local` file in the project root:

```
SMTP_HOST=smtp.gmail.com
SMTP_PORT=465
SMTP_SECURE=true
SMTP_USER=bmpoffice24x7@gmail.com
SMTP_PASS=zfuwotzpknxgawts
SMTP_FROM=bmpoffice24x7@gmail.com
CONTACT_RECEIVER_EMAIL=bmpoffice24x7@gmail.com
```

> **Note:** Never commit your `.env.local` file to version control. These credentials are sensitive.

After setting up, restart your development server for the changes to take effect.

---

## **How to Make the Contact Form Work**

### 1. **Add SMTP Credentials**

Create a file named `.env.local` in your project root (same level as `package.json`) and add the following:

```
SMTP_HOST=smtp.gmail.com
SMTP_PORT=465
SMTP_SECURE=true
SMTP_USER=bmpoffice24x7@gmail.com
SMTP_PASS=zfuwotzpknxgawts
SMTP_FROM=bmpoffice24x7@gmail.com
CONTACT_RECEIVER_EMAIL=bmpoffice24x7@gmail.com
```

> **Important:** Never commit `.env.local` to git. These credentials are sensitive.

---

### 2. **Restart Your Server**

After saving the `.env.local` file, restart your Next.js development or production server. This ensures the environment variables are loaded.

---

### 3. **How It Works**

- When someone submits the contact form, the frontend sends the data to `/api/contact`.
- The backend (`app/api/contact/route.ts`) uses Nodemailer to send an email to `CONTACT_RECEIVER_EMAIL` with the form details.

---

### 4. **Testing**

- Fill out the contact form on your site and submit.
- You should receive an email at `bmpoffice24x7@gmail.com` with the submitted details.

---

### 5. **Troubleshooting**

- If you don’t receive emails, check your spam folder.
- Make sure less secure app access is enabled for your Gmail account, or use an App Password (which you are already doing).
- Check your server logs for any errors.

---

**You are all set!**  
Let me know if you want to customize the email template, add validation, or need help with deployment.
