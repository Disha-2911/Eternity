# Eternity — Android E-commerce App

Eternity is a native Android shopping application built in **Java**. It turns a remote e-commerce API into a complete mobile buying flow: users can discover featured offers, browse categories and products, search the catalogue, manage a cart, submit an order, and continue to payment without leaving the app.

The project focuses on the practical building blocks of an Android commerce client: API-backed screens, image-heavy product listings, local cart state, checkout data collection, and a WebView-based payment hand-off.

## Features

- **Discover products** — a home screen with a featured-offer carousel, category grid, and recent-product grid
- **Category browsing** — open a category to view its available products
- **Catalogue search** — search products from the Material Search Bar
- **Product details** — view product imagery, pricing, availability, and HTML-formatted descriptions
- **Cart management** — add products to the cart, adjust quantities, and see the subtotal update
- **Checkout flow** — collect buyer, contact, address, and order-note details before submitting an order
- **Order confirmation and payment** — receive an order code and open the payment page inside the app
- **Remote content** — categories, products, offers, images, and order submission are all driven by an API

## Design decisions

- **API configuration in one place** — endpoint and image-base URLs live in `Constants.java`, keeping network configuration separate from the screens that use it.
- **RecyclerView for scalable listings** — reusable adapters render category, product, and cart data efficiently across the app.
- **View Binding instead of manual view lookup** — each activity uses generated binding classes for safer, cleaner UI access.
- **TinyCart for in-app cart state** — cart items and quantities stay available while the user moves through product, cart, and checkout screens.
- **WebView for the payment hand-off** — after order submission, the server-provided payment URL opens in the app instead of interrupting the buying flow with an external browser.

## Tech Stack

| Layer | Technology |
| --- | --- |
| Language | Java 8 |
| Platform | Android SDK (compile/target SDK 33) |
| UI | Android Views, View Binding, Material Components, ConstraintLayout |
| Lists | RecyclerView with GridLayoutManager and LinearLayoutManager |
| Networking | Volley |
| Image loading | Glide |
| Cart | TinyCart |
| Search | MaterialSearchBar |
| Offers | WhyNotImageCarousel |
| Payment | Advanced WebView |
| Testing | JUnit 4 |

## Project Structure

```text
Eternity/
├── app/
│   └── src/main/
│       ├── java/com/example/myapplication/
│       │   ├── activities/       # Home, search, product, cart, checkout, payment
│       │   ├── adapters/         # RecyclerView adapters for products, categories, cart
│       │   ├── model/            # Product and Category models
│       │   └── utils/
│       │       └── Constants.java # API and image endpoint configuration
│       ├── res/
│       │   ├── layout/           # Activity, item, and dialog layouts
│       │   ├── drawable/         # Icons and visual resources
│       │   └── values/           # Strings, colours, themes, fonts
│       └── AndroidManifest.xml
├── gradle/                       # Gradle wrapper
├── build.gradle                  # Project build configuration
└── settings.gradle
```

## Getting Started

### 1. Prerequisites

- Android Studio
- **JDK 11 or newer** for Gradle/Android Gradle Plugin compatibility
- Android SDK Platform 33
- An Android emulator or a physical device running Android 6.0 (API 23) or newer

### 2. Clone the repository

```bash
git clone https://github.com/Disha-2911/Eternity.git
cd Eternity
```

### 3. Open and run

1. Open the project folder in Android Studio.
2. Let Gradle finish syncing the project dependencies.
3. Select an emulator or connected Android device.
4. Run the `app` configuration.

The application requires an internet connection because catalogue data, offers, product images, order processing, and payment content are loaded from a remote service.

### Build a debug APK

From the project root:

```bash
./gradlew assembleDebug
```

On Windows:

```bat
gradlew.bat assembleDebug
```

The debug APK is generated at:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## How the shopping flow works

1. **Home** loads the latest offers, categories, and products from the API.
2. **Search or browse** opens a filtered product list or a category-specific catalogue.
3. **Product detail** fetches the full product record and lets the user add it to the cart.
4. **Cart and checkout** calculate the subtotal, apply the configured tax, and collect order information.
5. **Payment** submits the order, receives an order code, and loads the matching payment page in the app.

## API Configuration

The remote API is configured in:

```text
app/src/main/java/com/example/myapplication/utils/Constants.java
```

That file centralizes endpoints for categories, products, offers, product details, order submission, payment, and remote image directories. Replace the `API_BASE_URL` value there to connect Eternity to a different compatible backend.

## Running Tests

```bash
./gradlew testDebugUnitTest
```

The project has been verified to build successfully with `assembleDebug` and run its debug unit-test task using Android Studio's bundled JDK 11.

## Possible Extensions

- Add user accounts and order history
- Persist carts across app restarts
- Add wishlist and product-rating functionality
- Introduce pagination, filters, and sort controls for larger catalogues
- Add robust loading, empty-state, and network-error UI
- Move API configuration to build variants or environment-specific settings
- Add instrumented UI tests and a GitHub Actions Android build workflow

## Author

**Disha Agarwal**
