# Task 3 — Answers

## 1. What does the `visible` prop of `Modal` do and why do we control it with `useState`?

The `visible` prop decides whether the modal is shown (`true`) or hidden (`false`). We control it with `useState` because React Native redraws the screen when the state changes, so calling `setModalVisible(true)` or `setModalVisible(false)` opens or closes the modal.

## 2. What is `onRequestClose` for? What happens on Android if you do not close the modal in it?

`onRequestClose` runs when the user presses the Android back button (or the equivalent system gesture) while the modal is open. If it does not close the modal, the back button does nothing and the user feels stuck, so I use `onRequestClose={closeModal}`.

## 3. What is the effect of `transparent={true}`? Name the three values of `animationType`.

With `transparent={true}` the modal does not fill the screen with a white background, so I can see the screen behind it and build my own dark overlay and card. The three values of `animationType` are `none`, `slide` and `fade`.

## 4. Why does `ScrollView` exist? What happens with a long `View` without it? When would you choose `FlatList` instead?

`ScrollView` lets the user scroll content that is bigger than the screen. A long `View` without it is simply cut off and the user cannot see the rest. I would choose `FlatList` for long or unknown-size lists, because it renders only the items that are visible, while `ScrollView` renders everything at once.

## 5. What is the difference between the `style` and the `contentContainerStyle` props of a `ScrollView`?

`style` styles the `ScrollView` itself, the outer frame that has a fixed size on the screen (for example `flex: 1` or `maxHeight`). `contentContainerStyle` styles the inner container that holds the children, which is the part that scrolls (for example `padding`, `gap` or `flexGrow`).

## 6. What is `SafeAreaView` for and which zones of the device does it protect? Why do we use `react-native-safe-area-context`?

`SafeAreaView` adds padding so the content does not go under the notch, the status bar, the rounded corners or the home indicator at the bottom. We use `react-native-safe-area-context` because it works on both iOS and Android and it is the recommended library in Expo, while the `SafeAreaView` from `react-native` is deprecated and only works on iOS.

## 7. Write the three best practices from the Step 5 checklist in your own words and give an example of when a modal is **not** a good idea.

First, use only one modal on the screen and only for a short, focused action, like choosing contacts to share a profile. Second, keep the content inside a `ScrollView` limited (here only 5 projects and 8 contacts) because it renders everything at once. Third, wrap the screen in a `SafeAreaView` so nothing is hidden by the notch or the system bars. A modal is not a good idea for long or complex flows, such as filling a long registration form, because the user loses context and it is better to use a normal screen.