# Intro

## Research Expo (React Native)

[Expo Official](https://expo.dev/go)

![type:video](https://www.youtube.com/embed/FdjczjkwQKE?si=1MovnbnF7mSZAaq4)

[expo create a new project](https://docs.expo.dev/get-started/create-a-project/)

```bash
npx create-expo-app@latest

# Start Expo APP
npx expo start

# or This also works which eventually starts expo start
npm start
```

???+ bug

    ```bash
    npm run andriod
    ```

| Method                  | Android Studio Needed? | Physical Device Support | Emulator Support     | Notes                               |
| ----------------------- | ---------------------- | ----------------------- | -------------------- | ----------------------------------- |
| Android SDK CLI         | No                     | Yes                     | Genymotion/SDK tools | Manual setup, more control          |
| Expo CLI                | No                     | Yes (Expo Go app)       | No (native modules)  | Easiest, but limited native support |
| Community CLIs (Ignite) | No                     | Yes                     | Yes                  | Depends on CLI, check documentation |

- [reactnative.dev, Get Started with React Native](https://reactnative.dev)

---

## Common Issue Solved

!!! error "uncaught error java lang exception incompatible sdk version expo sdk 53"

- [Upgrade Expo SDK](https://docs.expo.dev/workflow/upgrading-expo-sdk-walkthrough/#sdk-changelogs)

???+ success "[How to upgrade to the latest SDK version](https://docs.expo.dev/workflow/upgrading-expo-sdk-walkthrough/#how-to-upgrade-to-the-latest-sdk-version)"

    **1. Upgrade the Expo SDK**

    Install the new version of the Expo package:

    ```bast title="npm"
    # Install latest
    - npx expo install expo@latest

    # Install a specific SDK version (for example, SDK 52)
    - npx expo install expo@^52.0.0
    ```

    **2. Upgrade dependencies**

    Upgrade all dependencies to match the installed SDK version.

    ```bash title="bash"
    npx expo install --fix
    ```
