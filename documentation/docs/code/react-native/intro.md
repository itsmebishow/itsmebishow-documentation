## Install Expo CLI (Optional but recommended for beginners)

Expo is a framework and platform for universal React applications. It simplifies the setup and development process, especially for beginners.


???+ example

    -   Install Expo CLI globally:

        !!! bug "WARNING: The legacy expo-cli does not support Node +17. Migrate to the new local Expo CLI:"

        ```
        npm install -g expo-cli
        ```


    -   Create a New Expo Project

        ```bash
        # Create a new project using Expo CLI:
        expo init my-new-project
        ```

        Follow the prompts to choose a template. For a basic setup, the “blank” template is a good choice.


    -   Navigate to your project directory:

        ```bash
        cd my-new-project
        ```


    -   Start the development server:

        ```bash
        expo start
        ```

        This will start the Expo development server and open the Expo DevTools in your browser.


???+ danger

    ```bash
    sudo npm install -g expo-cli
    ```

    WARNING: The legacy expo-cli does not support Node +17. Migrate to the new local Expo CLI: https://blog.expo.dev/the-new-expo-cli-f4250d8e3421.

    (node:605277) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
    (Use `node --trace-deprecation ...` to show where the warning was created)
    "help" is not an expo command. See "expo --help" for the full list of commands.


???+ success

    As of the latest updates, the `create-expo-app` tool, like other tools in the JavaScript ecosystem, is compatible with a range of Node.js versions. However, it's always a good practice to use a stable and supported Node.js version to avoid compatibility issues.

    > Supported Node.js Versions for `create-expo-app`
    
    1.  **LTS (Long-Term Support) Versions**:
    
        `create-expo-app` generally supports Node.js LTS versions. LTS versions are recommended for stability and compatibility with various tools. As of now, the commonly supported LTS versions are:

        -   Node.js 18.x (Gallium): This is the current LTS release.
        -   Node.js 16.x (Fermium): This was the previous LTS version.
    
    2.  **Current Stable Version**:
    
        While LTS versions are preferred, `create-expo-app` might also support the most recent stable Node.js versions. However, using the latest release (current version) might sometimes lead to unexpected issues if the tool or its dependencies are not yet fully compatible.


    > Recommendations

    -   Use Node.js LTS Versions:
    
        For maximum compatibility and stability, use the current LTS version of Node.js. As of the latest guidance, Node.js 18.x is the recommended version.

    -   Verify Compatibility:
    
        Always check the [Expo documentation](#) or the [Expo CLI GitHub repository](#) for any specific version requirements or known issues related to Node.js versions.
    


---


## How to Manage Node.js Versions

To manage and switch between different Node.js versions, you can use Node Version Manager (nvm):

1.  Install `nvm` (if not already installed):

    ```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
    ```

    Then load `nvm`:

    ```bash
    source ~/.nvm/nvm.sh
    ```



2.  Install and Use a Specific Node.js Version:

    ```bash
    nvm install 18
    nvm use 18
    ```

    Replace `18` with the desired version number.


3.  Check Installed Node.js Versions:

    ```
    nvm ls
    ```


---


## Steps to Create an Expo App


1.  Ensure Node.js Version: Verify you are using a compatible Node.js version:

    ```
    node -v
    ```


2.  Create a New Expo Project using create-expo-app:

    ```
    npx create-expo-app MyNewApp
    ```


---


## Running an Expo Project


If you used `npx` to create an Expo project using `create-expo-app` or a similar command, follow these steps:


1.  Navigate to Your Project Directory

    ```
    cd MyNewApp
    ```

    Replace `MyNewApp` with your project's directory name.


2.  **Start the Expo Development Server**

    Start the Expo development server by running:

    ```bash
    npm start
    ```

    or

    ```bash
    npx expo start
    ```

    This will start the Expo development server and open the Expo DevTools in your browser. You will see a QR code that you can scan with the Expo Go app to view your project on your mobile device.




---

## Set Up a Development Environment `Without Expo` (Optional)

If you prefer not to use Expo and want more control, you can set up a React Native development environment directly:


???+ info "For macOS and Linux:"

    -   **Install Watchman** (a tool used for watching changes in the filesystem):

        ```bash
        brew install watchman
        ```
    
    ---
    
    -   **Install the React Native CLI globally:**

        ```bash
        npm install -g react-native-cli
        ```
    
    -   **Create a New React Native Project**

        ```bash
        # Create a new project using React Native CLI:
        npx react-native init my-react-native-app

        # Navigate to the Project Directory
        cd my-react-native-app
        ```
    
    -   **Start the Development Server**

        ```bash
        # Start the Metro bundler:
        npx react-native start
        ```

        In a new terminal window, run the app on iOS or Android:


        -   iOS (macOS only):

            ```bash
            npx react-native run-ios
            ```
        
        -   Android:

            ```bash
            npx react-native run-android
            ```