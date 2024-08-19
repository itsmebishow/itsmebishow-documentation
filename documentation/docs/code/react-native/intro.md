## Install Expo CLI (Optional but recommended for beginners)

Expo is a framework and platform for universal React applications. It simplifies the setup and development process, especially for beginners.


???+ example

    -   Install Expo CLI globally:

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