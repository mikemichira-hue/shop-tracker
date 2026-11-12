../README.md# Shop Tracker

A simple web app for small shops in Kenya to manage **stock, sales and customer debts** in one place. It works on a phone or a laptop, and each shopkeeper's data is saved online under their own login.

**Live demo:** https://shop-tracker-770b6.web.app

## Features

- **Login for every shop:** sign up, log in and reset a forgotten password. Each account sees only its own data.
- **Stock:** add, edit, restock and delete items, with low-stock alerts and search and filters by category and status.
- **Sales:** record cash, M-Pesa or credit sales. Stock goes down automatically, and a sale can be undone.
- **Debts:** customers' balances, part-payments, and old debts from before the app.
- **Reports:** sales and profit for the last 7 days, last 30 days or this month, with a bar chart, best sellers, and items that are not selling.
- **Receipts:** print or save a receipt for any sale, with your shop's name on it.
- **Shop types:** grocery, hardware, general shop, pharmacy or other, each with its own categories and units.
- **English and Kiswahili:** switch language at any time.
- **Download your data:** stock, sales and debts as files that open in Excel or Google Sheets.
- **Works on phones:** a bottom tab bar on small screens and a sidebar on laptops.

## Built with

- HTML, CSS and JavaScript (no framework)
- Firebase Authentication for logins
- Cloud Firestore for saving data online
- Firebase Hosting for the live site

## Project structure

```
shop-tracker/
  public/
    index.html     the whole app (HTML, CSS and JavaScript)
    images/        pictures for the home page
  firebase.json    Firebase Hosting settings
  README.md
```

## Run it on your computer

1. Download or clone this repository.
2. Open the folder in VS Code and install the **Live Server** extension.
3. Right-click `public/index.html` and choose **Open with Live Server**.

The app talks to the Firebase project in the code. To run your own copy, create a project at [firebase.google.com](https://firebase.google.com), turn on **Email/Password** sign-in and **Firestore**, and replace the `firebaseConfig` values near the top of the script in `public/index.html`.

## Database rules

Each user can read and write only their own record:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /shops/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Deploy

```
npm install -g firebase-tools
firebase login
firebase deploy --only hosting
```

## Screenshots

<!--
Upload your screenshots to a "screenshots" folder, then remove the arrows around the lines below.

![Home page](screenshots/home.png)
![Stock page](screenshots/stock.png)
![Reports](screenshots/reports.png)
-->

## Ideas for later

- M-Pesa payments and monthly subscriptions
- More shop types and more languages
- Split large shops' data across several records

## Author

Built by **Micah Michira Nyabayo** (codewithmike).

- GitHub: [@mikemichira-hue](https://github.com/mikemichira-hue)
- Instagram: [@major.mic](https://instagram.com/major.mic)
- TikTok: [@pecanpoint](https://www.tiktok.com/@pecanpoint)
