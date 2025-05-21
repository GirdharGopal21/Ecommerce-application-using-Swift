# Ecommerce-application-using-Swift

![image alt](https://github.com/GirdharGopal21/Ecommerce-application-using-Swift/blob/8e5b127cf7dbaae0561b5214a03b84c04a7a0b83/eCommerce.png)

Xcode project built in SwiftUI relating to an eCommerce app showcasing fashion products and enabling users to :

=>create an account or login to an existing account

=>browse the product catalog

=>add/remove items to/from their favorites list

=>add/remove items to/from their cart

=>proceed with payment

=>view orders history

=>Project using Firebase and Stripe API.

=>App architecture : Repository Design Pattern


Usage

Open the eCommerce.xcodeproj file with Xcode and build the application in the simulator or on a device.


Swift Package Manager dependencies

Firebase


This project uses several libraries provided by Firebase SDK for iOS platforms 


=>Authentication : email and password based authentication

=>Cloud Firestore : products and users data storage through collections and documents

=>Cloud Storage : products images upload

=>Analytics : for logging events that provide insight on app usage and user engagement

=>Remote Config : used to change the colors of the app without publishing an app update

=>Stripe API

=>This project embeds Stripe iOS SDK and in particular the StripePaymentSheet module which provides a prebuilt payment UI.


The payment method integration uses three Stripe API objects :


PaymentIntent : represents the intent to collect payment from a customer during the Checkout process. Charge attempts and payment state changes are tracked throughout the process.

Customer : the Customer object is created during the Sign Up process.

Customer Ephemeral Key : grants the SDK temporary access to the Customer.

For security reasons, Stripe does not allow the app to create these objects. Instead, this has to be done on a server-side (see related section below).


*Note

Stripe provides test cards numbers allowing to test the integration through various scenarios.

For instance, filling out the credit card form using the credit card number 4242 4242 4242 4242 with any expiration in a future date, CVC, and postal code should lead to a payment success.


*Alamofire

This project uses Alamofire library to ease HTTP requests between the app and the server.


*Backend server

As mentioned above, Stripe requires a server-side implementation.

The server in this project is hosted on Glitch and has two endpoints.


The /customers endpoint creates the Customer object.

Additionally, as stated on Stripe setup, the /checkout endpoint :


retrieves the Customer

creates an Ephemeral Key for the Customer

creates a PaymentIntent, with the amount, currency, and customer

returns the Payment Intent’s client secret, the Ephemeral Key’s secret, the Customer’s id, and the publishable key to the app.


*Note

For performance purposes, Glitch’s projects sleep after 5 minutes. Therefore, one may experience delay when interacting with the app during the processes involving calls to the server (i.e. Sign Up & Checkout).


*Database

Under the path eCommerce/Utilities/ProductData, you can find :

a folder /database containing the datasets set up from scratch that have been used in this project

a file ProductDataManager.swift defining the methods that have been used to load the data in Firestore

For app leightweihting purpose, the images uploaded in Firestore have not been embedded in this project. However they can be retrieved within the file ProductDatabase.swift since the urls related to these images have been added to the ProductVariant model.

*Note

Security Rules for both Firestore and Storage have been setup in the Firebase console.
