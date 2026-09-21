# Eternity

Eternity is a native Android shopping app that lets users browse product categories and featured offers, search a product catalogue, manage a cart, place an order, and continue to payment.

## Features

- Featured-offer carousel on the home screen
- Product categories and latest-product grids
- Product search and product-detail views
- Shopping cart with quantity updates and subtotal calculation
- Checkout and in-app payment page
- Remote catalogue, images, and orders provided through the configured e-commerce API

## Tech stack

- Java and Android Views with View Binding
- AndroidX, Material Components, and ConstraintLayout
- Volley for API requests
- Glide for image loading
- TinyCart for cart management
- Advanced WebView for payment content

## Requirements

- Android Studio
- JDK 11 or newer (Android Gradle Plugin 7.3.0 requires Java 11+)
- Android SDK 33
- An Android emulator or a physical Android device

## Run locally

1. Clone the repository:

   ```bash
   git clone https://github.com/Disha-2911/Eternity.git
   ```

2. Open the project in Android Studio.
3. Allow Gradle to sync dependencies.
4. Select an emulator or connected device and run the `app` configuration.

You can also build a debug APK from the project root:

```bash
./gradlew assembleDebug
```

On Windows, use:

```bat
gradlew.bat assembleDebug
```

The generated APK is placed in `app/build/outputs/apk/debug/`.

## API configuration

The app reads its product data, offers, images, order submission, and payment URL from the base endpoint declared in:

`app/src/main/java/com/example/myapplication/utils/Constants.java`

Update that file if you want to point the app at your own backend.

## Testing

Run the unit tests with:

```bash
./gradlew testDebugUnitTest
```

## Notes

The app needs internet access to load the remote catalogue and payment content.
