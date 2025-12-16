# 🎨 Android Basic UI & Layouts Demo

A comprehensive Android application designed to teach students the fundamentals of Android User Interfaces (UI). This project demonstrates how to use common UI widgets, handle user input, manage layouts programmatically, and navigate between activities while passing data.

---

## 🚀 Features Overview

This app consists of three distinct activities, each focusing on a different aspect of Android development:

### 1. Main Dashboard (`MainActivity`)
* **Input Handling:** Demonstrates `TextInputEditText` for text, `CheckBox` for booleans, `RadioGroup` for single-choice options, and `Spinner` for dropdowns.
* **Material Design Components:** Uses `SwitchMaterial` for toggling Dark Mode and `Slider` for adjusting font size dynamically.
* **State Management:** Updates the UI in real-time based on user interaction (e.g., changing text size).

### 2. Layout Playground (`LayoutActivity`)
* **Dynamic UI Generation:** Instead of using XML, this activity generates layouts **programmatically** using Kotlin code.
* **Layout Comparison:** Allows users to switch between 6 different layout types via a dropdown to see how they behave differently:
    * `LinearLayout` (Vertical & Horizontal)
    * `RelativeLayout`
    * `ConstraintLayout`
    * `GridLayout`
    * `TableLayout`

### 3. Data Passing (`SecondActivity`)
* **Intents:** Demonstrates how to navigate from one screen to another.
* **Bundle Extras:** Shows how to retrieve data passed from the previous activity (the greeting message and font size preferences).

---

## 🛠 Tech Stack

* **Language:** Kotlin
* **UI Toolkit:** Standard Android Views (XML + Programmatic)
* **Design System:** Material Design 3
* **Navigation:** Android Intents

---

## 🧑‍💻 Code Highlights

### Dynamic Layouts (`LayoutActivity.kt`)
This file is excellent for understanding how layouts work "under the hood." Instead of inflating an XML file, we create views in code.

**Example: Creating a Linear Layout Programmatically**
```kotlin
private fun createVerticalLinearLayoutDemo(): LinearLayout {
    return LinearLayout(this).apply {
        orientation = LinearLayout.VERTICAL
        // Define width and height
        layoutParams = FrameLayout.LayoutParams(
            FrameLayout.LayoutParams.MATCH_PARENT,
            FrameLayout.LayoutParams.MATCH_PARENT
        )
        // Add children views...
        addView(TextView(context).apply { text = "I was made in Kotlin!" })
    }
}

```

### Passing Data Between Activities (`MainActivity.kt`)
We use `Intents` to move data.

```kotlin
val intent = Intent(this, SecondActivity::class.java).apply {
    // Key-Value pairs
    putExtra("GREETING_MESSAGE", message)
    putExtra("FONT_SIZE", fontSizeSlider.value)
}
startActivity(intent)

```

### Receiving Data (`SecondActivity.kt`)

```kotlin
// Retrieve data using the same keys
val message = intent.getStringExtra("GREETING_MESSAGE")
val fontSize = intent.getFloatExtra("FONT_SIZE", 18f) // 18f is the default
```

---

## 📱 How to Run
1. **Clone the repository** and open it in **Android Studio**.
2. **Resource Check:** Ensure your `res/values/strings.xml` contains the array for the spinner (see note below).
3. **Sync Gradle** to ensure Material Design dependencies are loaded.
4. **Run the app** on an emulator or physical device.

### ⚠️ Important: Setup Requirement
The `MainActivity.kt` references a string array resource for the titles dropdown. You must ensure this exists in your `res/values/strings.xml` file, or the app will crash on launch.

**Add this to `strings.xml`:**

```xml
<resources>
    <string name="app_name">BasicUI Demo</string>
    
    <string-array name="titles_array">
        <item>Mr.</item>
        <item>Ms.</item>
        <item>Mrs.</item>
        <item>Dr.</item>
        <item>Mx.</item>
    </string-array>
</resources>

```

