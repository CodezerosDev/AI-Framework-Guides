## **<span style="text-decoration:underline;">Introduction to Prompt Engineering for React Native</span>**


### **1. Be Specific About Component Type**

**Cursor prompt** 👍 : **Create a list component**

**<span style="text-decoration:underline;">Feedback : </span>**



* `List&lt;T>` with TypeScript — ensures proper typing for `data` and `renderItem`.
* Better UI by default for clean lists
* Automatic empty list styling (`emptyContainer` style) + `emptyComponent`.
* You don't have to keep repeating FlatList props all over your app.

**<span style="text-decoration:underline;">Challenges : </span>**



* Advanced FlatList props like `onEndReached`, `refreshControl`, `horizontal`, `numColumns`, etc. aren't exposed here yet.
* If a screen needs very simple FlatList usage, this wrapper might feel like unnecessary extra work.
* If `renderItem` crashes (e.g., bad item type), there's no fallback or error catcher inside the list.
* `List` and `FlatList` aren't memoized. So if `data` updates, the full `List` re-renders. 

**Cursor prompt** 👍 :  **Create a React Native FlatList component that displays user profiles with images, names, and status indicators. Include pull-to-refresh functionality, infinite scrolling with activity indicator, and empty state handling. The component should be optimized for performance with appropriate item recycling.**

**<span style="text-decoration:underline;">Feedback : </span>**



* Graceful fallback (No profiles found) when list is empty.
* Integrated `RefreshControl` — perfect for refreshing latest profiles.
* Used `useCallback` correctly to avoid unnecessary re-renders (`handleRefresh`, `handleLoadMore`, `renderItem`).
* Strong typing (`UserProfile`, `UserProfileListProps`) ensures safe usage.
* Dynamically shows colored dot based on user status (online/away/offline).

**<span style="text-decoration:underline;">Challenges :</span>**



* `flex: 1` might stretch the empty state unnaturally if list is embedded in a non-flex layout.
* Assumes `item.id` always exists and is unique — should ideally validate or fallback safely.
* Spinner color `"#0000ff"` is hardcoded — better to pass it as a prop for custom theming.
* Basic `&lt;Image />` is used — no caching logic (like `react-native-fast-image`) for better image loading performance.
* No feedback if onRefresh or onLoadMore fail — no error state UI.
* Hardcoded to `0.5` — in some apps, you might want customizable thresholds.


### **2. Include State Management Context**

**Cursor prompt** 👍 : **Generate code for a login screen**

**<span style="text-decoration:underline;">Feedback : </span>**



* Uses ActivityIndicator and disables the login button while loading,
* Uses `KeyboardAvoidingView` based on platform (`padding` for iOS, `height` for Android) — crucial for preventing the keyboard from hiding inputs.
* Displays individual error messages under each input if validation fails.

**<span style="text-decoration:underline;">Challenges : </span>**



* It doesn’t give login flow with redux or any state management.
* Unhandled **Forgot Password** and **Signup** Navigation
* No Password Show/Hide Toggle
* Hardcoded Colors and Style Duplication
* No Global Error Handling
* No Form Reset after Success
* When you tap outside the `TextInput`, the keyboard stays open.
* It is not using React Hook Form’s `Controller` pattern, wrapping a custom input (`InputBox`) instead of using a plain `&lt;TextInput>`.

**Cursor prompt** 👍 :** Generate a React Native login screen using Redux for state management. The screen should include email and password fields with validation, a submit button with loading state, error handling for authentication failures, and "Forgot Password" functionality. Use Redux actions and reducers for handling the authentication flow.**

**<span style="text-decoration:underline;">Feedback : </span>**



* It make perfect structure of redux tool kit for state management - 
* Store

            index.ts


             -	types


            auth.ts

* Reducer

                authReducer.ts

* Component

                LoginScreen.tsx.

* Modular structure if Redux actions, reducers, and types are separated neatly.
* Authentication **error handling** (e.g., displaying "Invalid credentials" on failure) is well integrated.

 

**<span style="text-decoration:underline;">Challenges : </span>**



* Input keyboard handling (like dismissing the keyboard on submit or tapping outside inputs) is missing.
* If **navigation** from the "Forgot Password" button is not properly wired up ,  it leaves the functionality incomplete.
* If the **loading spinner** is not disabled properly after a failed attempt, it could lead to a stuck UI.
* If **form validation** is done manually (e.g., with simple if-checks) instead of using a **library like Yup + Formik**, it can lead to messy, unscalable code.
* If **error messages** are too generic (like "Something went wrong" without specifics), it's less user-friendly.


### **3. Define Platform-Specific Requirements**

**Cursor prompt** 👍**: Create a notification component**

**<span style="text-decoration:underline;">Feedback :</span>** 



* Create a reusable notification component that can display different types of notifications (success, error, warning, info) with animations and auto-dismiss functionality.
*  Its using React Native's Animated API for smooth transitions.

**<span style="text-decoration:underline;">Challenges : </span>**



* Its not using libraries like Notifee, no heavy logic.

**Cursor prompt** 👍**: Create a React Native notification system that handles both iOS and Android notifications appropriately. Include logic for requesting permissions, token registration, and notification handling for both foreground and background states. For iOS, handle the required permission flow, and for Android, include the necessary channel creation code. Use react-native-notifications package.**

**<span style="text-decoration:underline;">Feedback :</span>** 



* Proper platform-specific handling (separating iOS and Android logic) is a strong point for robustness.
* There’s **error handling** for permissions denied, token errors, etc., it improves the reliability of the app.
* Using react-native-notifications simplifies native bridging while maintaining customization control — good library choice.
* If **requesting permissions** (especially for iOS — alert, sound, badge) is handled properly, it shows attention to iOS policies.
* Foreground and background **notification event listeners** (onNotificationOpened, onNotificationReceivedForeground) are cleanly implemented — a big plus.
* **Android notification channel creation** (importance, vibration patterns, sound options) shows good understanding of requirements.

**<span style="text-decoration:underline;">Challenges : </span>**



* Clean-up of listeners on unmount (removeEventListener) is not implemented which leads to memory leak.
* If **token refresh events** (onTokenRefresh) are not listened for, push notifications might silently fail later.
* If **deep linking or navigation handling** after notification tap is missing.
* No **log tracking** for notification receipt, tap, and dismiss events makes debugging very difficult later.


### **4. Specify Package Dependencies**

**Cursor Prompt **👍**: Create navigation code**

**<span style="text-decoration:underline;">Feedback :</span>** 



* Strong typing using RootStackParamList and BottomTabParamList ensures safe, predictable navigation.
* Clean split between `Stack.Navigator` and `Tab.Navigator`, which keeps it maintainable.
* `BaseScreen` manages `SafeAreaView`, `StatusBar`, and background — super reusable and flexible.
* `ThemeContext` correctly uses system theme and allows manual toggling.
* Top-level `NavigationContainer` wraps the app navigation properly.
* `headerShown`, `animation`, titles, and back button text customized for Stack screens.
* No unnecessary re-renders since context/state is correctly scoped.

**<span style="text-decoration:underline;">Challenges : </span>**



* ChatScreen appears inside both TabNavigator (Chat tab) and StackNavigator (Chat with params) — might cause navigation conflicts or unexpected behaviors.
* `initialRouteName="Onboarding"` is hardcoded
* Theme is not passed to `NavigationContainer` (`theme={navigationTheme}`) — so the navigation bar will always be default styled (light).
* No `accessibilityLabel` or `testID` props in buttons or tabs — not a major issue but could help for better accessibility/testing.

**Cursor Prompt **👍**:Create a React Native navigation setup using React Navigation v6 with a bottom tab navigator, drawer navigator, and stack navigator. Include type definitions for TypeScript, custom header components, and navigation params. Set up deep linking configuration and navigation state persistence using AsyncStorage.**

**<span style="text-decoration:underline;">Feedback :</span>** 



* Separating `Auth`, `Main`, and `Drawer`, plus individual `Stack` and `Tab` navigators, makes it easy to add more features later (like admin panels, onboarding flows, etc.) without needing to rewrite routing logic.
* `CustomHeader` lets you easily customize the header (colors, title, buttons) without touching screen components individually.
* Authenticated vs unauthenticated flows are neatly separated (`AuthNavigator` &  `DrawerNavigator`) 

**<span style="text-decoration:underline;">Challenges : </span>**



* Having Stack + Tabs + Drawer nested increases navigation depth
* **Reading AsyncStorage at startup**, which can cause **slower app launch times** and **State corruption** if AsyncStorage fails .
* As your app grows, **updating the linking config** becomes tedious and error-prone. Every new screen addition will require **manual updating** inside the `linking` object.


### **5. Describe Desired Styling Approach**

**Cursor Prompt **👍**: Style a button**

**<span style="text-decoration:underline;">Feedback :</span>** 



* created a reusable styled button component that follows modern design principles.
* **Clean separation of concerns** — button styles and text styles are organized separately (`getButtonStyle`, `getTextStyle`).
* **Disabled state** properly managed — disables touch and visually reduces opacity.
* **Platform-specific styling** — uses `Platform.select` for iOS shadows and Android elevation correctly.
* **Use of TypeScript** — types/interfaces (`StyledButtonProps`, union types for variants and sizes) increases code robustness.

**<span style="text-decoration:underline;">Challenges : </span>**



* The button style is hardcoded (fixed width/height/colors without flexibility), it reduces reusability.
* No handling for **different screen sizes/responsive layouts** can cause the button to appear too big or too small depending on device.
* **Icons not properly spaced** — If `leftIcon` or `rightIcon` are provided, there’s no margin between the icon and the text, which could make the button content look crowded.
* **No memoization for style calculations** —

    `getButtonStyle` and `getTextStyle` are functions that recompute on every render. Could optimize using `useMemo` to avoid unnecessary recalculations.

* If a wrong variant string is accidentally passed, it could crash or silently fail since `styles[variant]` is dynamically accessed.

**Cursor Prompt **👍**: Create a custom React Native button component using styled-components. The button should have primary, secondary, and disabled states with appropriate color transitions. Include proper ripple effects on Android and opacity animations on iOS. Make it support various sizes (small, medium, large) and include icons as an optional prop.**

**<span style="text-decoration:underline;">Feedback :</span>** 



* Proper ripple effect on Android —

    On Android, uses TouchableOpacity with activeOpacity=0.7, a standard native feel for presses

* Excellent use of `styled-components` —

    `ButtonContainer`, `ButtonText`, and icon containers are cleanly separated, making the button highly customizable and readable.

* **Full-width option** —

    Supports `fullWidth` prop to allow the button to stretch across available space — very useful in responsive layouts.

* **Custom icons support** — Accepts **left** and **right** icons as props with automatic sizing and color adjustment based on button size and variant.
* **Dynamic and reusable** — A developer could easily add more button variants, sizes, or icons without changing core logic.
* Shows an `ActivityIndicator` instead of text during loading. Also dims the button when disabled using `opacity`.
* Accepts **left** and **right** icons as props with automatic sizing and color adjustment based on button size and variant.

**<span style="text-decoration:underline;">Challenges : </span>**



* Colors (`white` or `#007AFF`) are fixed based on primary variant check. Could improve by dynamic coloring based on `variant` for better consistency.
* Full background press animation not visible on Android.
* ​​No pressed color change on Android - While iOS has a scale animation, Android could benefit from a ripple or pressed background effect — currently, just opacity change.
* TouchableOpacity placed incorrectly for full button tap - ideally, `TouchableOpacity` should wrap everything together — so entire button (including margins, animations) reacts to taps.


### **6. Other**

**<span style="text-decoration:underline;">Task : Language localization for react-native</span>**

**Cursor prompt** 👍

can u please do language localization for english,french and dutch please use

npm install i18next react-i18next

nd also made sepreate file for all the language and change all the UI pages for translation and set default language as english.

**<span style="text-decoration:underline;">Feedback</span>**

I'll help you set up internationalization (i18n) for your React application using i18next and react-i18next. Let's break this down into steps:



* First, let's install the required packages
* Create language files
* Set up the i18n configuration
* Modify the UI components to use translations

npm install i18next react-i18next

Now, let's create a directory structure for our translations. 

mkdir -p src/locales/en src/locales/fr src/locales/nl

**<span style="text-decoration:underline;">Challenges</span>**



* Could not find file 'src/App.js'.
* cursor is not able  to change my component file.It give just this kind of example how to change in component file.

    Import the `useTranslation` hook in any component where you need translations:


    import { useTranslation } from 'react-i18next';


    Use the hook in your component


    const { t } = useTranslation();


**Cursor prompt** 👍

can u please update onboarding/page.tsx and login/page.tsx as per language localization.



* It started changing my files and do required changes along with cursor changed my UI design also.that looks too ugly. \
Then again i gave prompt

    **Cursor prompt** 👍


    update onboarding/page.tsx and login/page.tsx as per language localization but why r u changing my design and UI please dont change that without my concern

* Cursor completely fails to do so.It is not able to change my UI back.
* What i noticed also  \
If i gave same prompt again than it give different outcome not the same.

**<span style="text-decoration:underline;">Task : Email validation using yup</span>**

**Note : **without prompt cursor doing normal validation .


    **Cursor prompt** 👍

can u please do email validation using yup 

**npm install yup**

 It will modify the login page to use yup for email validation.


```
const loginSchema = yup.object().shape({
 email: yup
   .string()
   .email('Please enter a valid email')
   .required('Email is required'),
 password: yup
   .string()
   .min(6, 'Password must be at least 6 characters')
   .required('Password is required'),
});
```


**<span style="text-decoration:underline;">Challenges</span>**



* if i am not adding domain in my email textInput than it not showing validation msg

    Than again i give prompt - 


    **Cursor prompt** 👍


if i am not adding domain in my email than it not showing validation msg


```
const loginSchema = yup.object().shape({
 email: yup
   .string()
   .matches(
     /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
     'Please enter a valid email with domain (e.g., example@domain.com)'
   )
   .required('Email is required'),
 password: yup
   .string()
   .min(6, 'Password must be at least 6 characters')
   .required('Password is required'),
});
```


**<span style="text-decoration:underline;">Challenges</span>**



* They add regex directly without grouping.

 \

