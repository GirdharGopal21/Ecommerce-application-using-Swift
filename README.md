# 🛍️ SwiftUI Fashion eCommerce App

![image alt](https://github.com/GirdharGopal21/Ecommerce-application-using-Swift/blob/8e5b127cf7dbaae0561b5214a03b84c04a7a0b83/eCommerce.png)



A beautifully designed **eCommerce iOS application** built with **SwiftUI**, showcasing fashion products. Integrated with **Firebase** for backend services and **Stripe** for secure payment processing.

This project demonstrates best practices in iOS architecture using the **Repository Design Pattern**, ensuring scalability, testability, and separation of concerns.

---

## ✨ Features

* 🔐 **User Authentication** – Sign up / Login via email & password (Firebase Auth)
  
* 🛍️ **Product Catalog** – Browse through a stylish fashion product catalog
  
* ❤️ **Favorites** – Add or remove products from a favorites list
  
* 🛒 **Cart** – Manage cart items and proceed to checkout
  
* 💳 **Secure Payment** – Seamless checkout with Stripe Payment Sheet
  
* 📦 **Order History** – View past purchases and order details
  
* 🎨 **Remote Config** – Dynamically change app colors without updating the app
  
* 📊 **Analytics** – Gain insight into user behavior and engagement

---


## 🏗️ App Architecture

This app uses the **Repository Design Pattern**, which:

* Promotes clean separation between the UI and data layers
  
* Improves code maintainability and testability
  
* Facilitates easy integration with multiple data sources (Firestore, Storage, REST API)

---


## 🔌 Dependencies

### 🧩 Swift Package Manager

This project uses the following packages:

* **[Firebase SDK for iOS](https://firebase.google.com/docs/ios/setup)**:

  * Authentication
    
  * Cloud Firestore
    
  * Cloud Storage
    
  * Analytics
    
  * Remote Config

* **[Stripe iOS SDK](https://stripe.com/docs/payments/accept-a-payment?platform=ios)**:

  * `StripePaymentSheet` module for a seamless checkout UI

* **[Alamofire](https://github.com/Alamofire/Alamofire)**:

  * Simplifies HTTP networking between the app and backend server

---


## 🧾 Stripe Integration Details

Stripe integration uses three main objects:

* **PaymentIntent** – Represents the payment flow
  
* **Customer** – Created during sign up
  
* **Ephemeral Key** – Grants temporary SDK access to the customer
  

### ⚠️ Note:

Stripe requires server-side object creation. This project includes a simple backend hosted on **Glitch**.


#### 🔗 Server Endpoints:

* `/customers`: Creates a new Stripe Customer
  
* `/checkout`: Retrieves Customer, creates Ephemeral Key, PaymentIntent, and returns:

  * Client Secret
    
  * Ephemeral Key Secret
    
  * Customer ID
    
  * Stripe Publishable Key

📌 Test with Stripe card number: `4242 4242 4242 4242` (any future date, valid CVC & postal code)

---


## ☁️ Firebase Setup

* **Firestore**: Stores products, variants, user data
  
* **Cloud Storage**: Uploads product images
  
* **Remote Config**: Dynamically change app theme colors
  
* **Analytics**: Track app usage and events

Security rules have been configured in Firebase Console.

---


## 🗂️ Product Data

Located in: `eCommerce/Utilities/ProductData/`

* `/database/` – Contains initial product datasets
  
* `ProductDataManager.swift` – Loads product data into Firestore
  
* `ProductDatabase.swift` – Holds image URLs linked to product variants

🖼️ Note: Product images are **not embedded** to reduce app size. Image URLs are fetched from Firestore dynamically.

---


## 🚀 Getting Started

1. Clone the repository
   
2. Open `eCommerce.xcodeproj` in Xcode
   
3. Make sure you have configured Firebase properly in the project
   
4. Build and run on **iOS Simulator or a physical device**

---


## 🧪 Stripe Testing Cards

| Card Type     | Number                | Outcome            |
| ------------- | --------------------- | ------------------ |
| Visa          | `4242 4242 4242 4242` | Payment success    |
| 3D Secure     | `4000 0027 6000 3184` | Requires 3D Secure |
| Declined Card | `4000 0000 0000 9995` | Payment failed     |

---


## 🛠️ Backend Glitch Note

Glitch-hosted backend may sleep after 5 mins of inactivity, causing slight delays during **Sign Up** or **Checkout** operations.

---




