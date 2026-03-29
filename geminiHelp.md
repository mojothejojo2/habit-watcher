# installing rust on mac
To install Rust on a Mac, use the official toolchain installer, rustup, which is the recommended method for most developers. It manages the compiler (rustc), the package manager (cargo), and allows you to easily update your installation. [1, 2, 3, 4] 
1. Run the Installation Script [5] 
Open your Terminal (Applications > Utilities > Terminal) and enter the following command: [6] 

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

[1, 7] 
2. Configure the Installation

* Select Options: When the script runs, it will prompt you with options. Press 1 and then Enter to proceed with the default installation.
* Activate Environment: After the script finishes, you need to add Rust to your shell's PATH. You can do this by restarting your terminal or by running this command in your current session:

source "$HOME/.cargo/env"

[4, 8, 9, 10, 11] 

3. Install a Linker (C Compiler) [12] 
Rust requires a C compiler for its linker to function. If you don't already have one, install the Xcode Command Line Tools by running: [10, 13, 14] 

xcode-select --install

[7, 15] 
4. Verify the Installation
Check that both the Rust compiler and the package manager are correctly installed: [16, 17, 18] 

* rustc --version — Should return the version of the compiler.
* cargo --version — Should return the version of the package manager. [13, 18, 19, 20] 

Alternative Method: Homebrew
If you already use [Homebrew](https://brew.sh/), you can install Rust with a single command, though this method provides less flexibility for managing multiple toolchain versions compared to rustup: [18, 21] 

brew install rust

[18, 22] 
Useful Commands

* Update Rust: rustup update
* Uninstall Rust: rustup self uninstall
* Offline Documentation: rustup doc (opens the documentation in your web browser) [2, 4, 13, 19] 

Would you like to learn how to set up VS Code with the Rust-Analyzer extension to start coding?

[1] [https://rust-lang.org](https://rust-lang.org/tools/install/)
[2] [https://rust-lang.org](https://rust-lang.org/tools/install/)
[3] [https://rust-lang.org](https://rust-lang.org/tools/install/)
[4] [https://web.mit.edu](https://web.mit.edu/rust-lang_v1.25/arch/amd64_ubuntu1404/share/doc/rust/html/book/second-edition/ch01-01-installation.html)
[5] [https://github.com](https://github.com/rust-lang/rustup/issues/3458#:~:text=My%20personal%20recommendation%20for%20setting%20up%20a,toolchain%20via%20rustup%20toolchain%20link%20system%20.)
[6] [https://ports.macports.org](https://ports.macports.org/port/rustup/#:~:text=Instructions%20*%20To%20install%20rustup%2C%20run%20the,selfupdate%20&&%20sudo%20port%20upgrade%20rustup%20Copy.)
[7] [https://doc.rust-lang.org](https://doc.rust-lang.org/book/ch01-01-installation.html)
[8] [https://www.geeksforgeeks.org](https://www.geeksforgeeks.org/how-to-install-rust-in-macos/)
[9] [https://www.geeksforgeeks.org](https://www.geeksforgeeks.org/how-to-install-rust-in-macos/)
[10] [https://doc.rust-lang.org](https://doc.rust-lang.org/book/ch01-01-installation.html)
[11] [https://rust-lang.org](https://rust-lang.org/tools/install/)
[12] [https://doc.rust-lang.org](https://doc.rust-lang.org/book/ch01-01-installation.html#:~:text=It%20%28%20rust%2Dlang%20%29%20is%20likely%20you,code%20and%20will%20need%20a%20C%20compiler.)
[13] [https://doc.rust-lang.org](https://doc.rust-lang.org/book/ch01-01-installation.html)
[14] [https://users.rust-lang.org](https://users.rust-lang.org/t/brand-new-to-rust-stuck-already/84201#:~:text=Rust%20%28%20rust%2Dlang%20%29%20needs%20a%20working,to%20download%20the%20whole%2020+%20GB%20beast.)
[15] [https://doc.rust-lang.org](https://doc.rust-lang.org/book/ch01-01-installation.html)
[16] [https://notes.kodekloud.com](https://notes.kodekloud.com/docs/Rust-Programming/Getting-Started-with-Rust/Setting-up-the-Development-Environment/page#:~:text=Installing%20Rust%20with%20Rustup%20Once%20installed%2C%20verify,via%20your%20default%20web%20browser%2C%20run:%20Copy)
[17] [https://www.hostwinds.com](https://www.hostwinds.com/tutorials/install-rust-toolchain-linux-cloud-vps#:~:text=Step%205:%20Verify%20Installation%20%28Optional%29%20These%20commands,and%20verified%20Rust%20on%20your%20Linux%20system.)
[18] [https://dev.to](https://dev.to/yrizos/installing-rust-on-macos-with-homebrew-51fk)
[19] [https://www.mintlify.com](https://www.mintlify.com/rust-lang/rust/installation)
[20] [https://rust-lang.org](https://rust-lang.org/learn/get-started/#:~:text=To%20test%20that%20you%20have%20Rust%20and,choice:%20cargo%20%2D%2Dversion.%20Read%20the%20cargo%20book.)
[21] [https://dev.to](https://dev.to/xs/setting-up-rust-on-macos-in-a-clean-way-13d1)
[22] [https://formulae.brew.sh](https://formulae.brew.sh/formula/rust)


# error with the command `yarn task build`
The error Command "task" not found occurs because Yarn treats the word immediately following yarn as the command to execute. In your case, it is trying to find a built-in command or a script named "task," which doesn't exist by default. [1, 2] 
How to Fix the Command
Depending on what you are trying to achieve, use one of the following standard commands:

* To run a standard build script: Most projects simply use:

yarn build

This is a shortcut for yarn run build, which executes the build script defined in your package.json.
* To run a specific script named "task:build": If your project uses a colon-separated naming convention (common in monorepos or complex setups), run:

yarn task:build

* If you actually have a script literally named "task": You must pass the argument to it like this:

yarn task build

Note: This only works if "task" is defined in your scripts section of package.json. [1, 3, 4, 5, 6] 

Troubleshooting Your Setup
If yarn build also fails with a "not found" error, check these three things:

   1. Check package.json: Open your package.json file and ensure there is a scripts section that contains the command you are trying to run:
   
   "scripts": {
     "build": "next build",  // example
     "task:build": "some-other-command"
   }
   
   2. Verify Your Directory: Run ls to make sure you are in the root directory of your project (where the package.json file lives).
   3. Check Available Scripts: Run the following command to see a list of all valid scripts you can execute in your current project:
   
   yarn run
   
   [7, 8, 9, 10] 

Does your package.json show a specific script under a different name, such as compile or bundle? [6] 

[1] [https://stackoverflow.com](https://stackoverflow.com/questions/54693223/what-does-yarn-build-command-do-are-npm-build-and-yarn-build-similar)
[2] [https://stackoverflow.com](https://stackoverflow.com/questions/57215872/what-is-the-difference-between-yarn-build-and-yarn-install)
[3] [https://yarnpkg.com](https://yarnpkg.com/getting-started/usage)
[4] [https://yarnpkg.com](https://yarnpkg.com/getting-started/usage)
[5] [https://github.com](https://github.com/strapi/strapi-docker/issues/304)
[6] [https://yarnpkg.com](https://yarnpkg.com/cli/run)
[7] [https://stackoverflow.com](https://stackoverflow.com/questions/55789355/build-node-js-app-using-yarn-but-getting-error-command-build-not-found)
[8] [https://classic.yarnpkg.com](https://classic.yarnpkg.com/lang/en/docs/cli/run/)
[9] [https://stackoverflow.com](https://stackoverflow.com/questions/70818525/unable-to-run-yarn-run-build)
[10] [https://bitrise.io](https://bitrise.io/integrations/steps/yarn)


# after the build - where does the artifact reside? -- this is irrelevant and more relevant answer below
After running a build command via Yarn, the location of the resulting artifact depends entirely on the specific tool or framework your project uses. Yarn itself does not define a standard output directory; it simply executes the script defined in your package.json. [1] 
Common default locations based on project type include:

* Standard Web Apps (React, Vue, Vite): Typically in a /dist or /build folder at the root of your project.
* Next.js: Inside the hidden .next/ directory.
* Rust Projects (if using Yarn to wrap Cargo): Usually in the target/ directory, specifically target/debug/ or target/release/.
* Yarn.build Plugin: Often defaults to a dist/ folder, but can be explicitly set in your package.json under a "yarn.build" configuration key. [1, 2, 3, 4, 5, 6] 

How to Find Your Specific Path
To find exactly where your project is saving the build, check the scripts section of your package.json file. Look for the command that runs when you type yarn build. For example:

"scripts": {
  "build": "webpack --output-path ./my-custom-folder" 
}

In this example, your artifacts would be in ./my-custom-folder.
Can you share the scripts section from your package.json? I can then tell you the exact folder to look in. [1] 

[1] [https://stackoverflow.com](https://stackoverflow.com/questions/54693223/what-does-yarn-build-command-do-are-npm-build-and-yarn-build-similar)
[2] [https://www.reddit.com](https://www.reddit.com/r/reactjs/comments/hwuo60/is_there_a_way_to_change_the_dir_the_build_folder/)
[3] [https://github.com](https://github.com/ReactJSResources/react-webpack-babel/issues/302)
[4] [https://users.rust-lang.org](https://users.rust-lang.org/t/how-to-get-the-output-file-path-in-env/60155)
[5] [https://besmith43.github.io](https://besmith43.github.io/posts/RustCrossCompilation/)
[6] [https://github.com](https://github.com/ojkelly/yarn.build/blob/main/readme.md)


# get the exact command needed for the project to run?
To improve your command for the [n4ze3m/habit-watcher](https://github.com/n4ze3m/habit-watcher) project, you should use the scripts explicitly defined in its [package.json](https://github.com/n4ze3m/habit-watcher/blob/main/package.json). The project is built using Vite and TypeScript, and it does not contain a script named "task."
Recommended Command
To build the project for production, run:

yarn build

This command is a shortcut for tsc && vite build, which ensures your TypeScript code is type-checked before the Vite bundler creates the production assets.
Why "yarn task build" failed

* Command Parsing: Yarn interprets the first word after yarn as the script name. Since there is no script called "task" in this repository, it throws an error.
* Correct Syntax: If you were trying to pass an argument to a script named task, it would look like yarn task build. However, because this specific project uses standard Vite scripts, yarn build is the intended command.

Other Useful Commands for this Project
If you are developing locally, you might find these other scripts from the repo helpful:

* Development Mode: yarn dev (Starts the local Vite dev server)
* Preview Build: yarn preview (Boots up a local server to view your production build)

Where is the artifact?
After running yarn build, your compiled files will reside in the /dist folder at the root of the project.
Would you like to know how to deploy this /dist folder to a service like Vercel or GitHub Pages?


# After building the app - how to run it?
Once you build the [Habit Watcher](https://github.com/n4ze3m/habit-watcher) app, you will have a lightweight, privacy-focused desktop application designed to track daily routines through a visual interface. [1, 2] 
What the App Looks Like
The app features a modern, clean design centered around a visual progress system: [3, 4] 

* GitHub-style Contribution Graph: Your habit consistency is displayed as a grid of squares that change color based on your activity, similar to GitHub's commit history.
* Analytics Dashboard: You can view your current streaks, total days tracked, and any missed days.
* Minimalist Interface: It focuses strictly on habit logging without social distractions or complex sub-menus. [3, 5, 6, 7] 

How to Start the App
Because this project uses Tauri, there are two different ways to "start" it depending on whether you want to run it for development or launch the final built version: [8] 
1. Run in Development Mode (Easiest for testing) [8] 
If you just want to see the app running immediately without creating a standalone installer, run:

yarn tauri dev


* This starts a local development window.
* The app will automatically reload whenever you make changes to the code.

2. Run the Production Build
If you have already run the build command (yarn build or yarn tauri build), the app is compiled into a standalone macOS application: [9] 

* Find the executable: Navigate to your project folder: src-tauri/target/release/bundle/macos/.
* Launch it: Double-click the Habit Watcher.app file to start it like any other Mac application. [10] 

3. Preview the Web Version
If you only ran the frontend build (yarn build) and didn't use the Tauri wrapper, you can preview the web-based UI in your browser:

yarn preview

Would you like help customizing the contribution graph colors or adding your first habit to the list?

[1] [https://github.com](https://github.com/topics/habit-tracking?l=javascript&o=desc&s=forks)
[2] [https://github.com](https://github.com/sitek94/habit-tracker-app)
[3] [https://github.com](https://github.com/n4ze3m/habit-watcher)
[4] [https://github.com](https://github.com/n4ze3m/habit-watcher)
[5] [https://github.com](https://github.com/n4ze3m/habit-watcher)
[6] [https://madewithtauri.com](https://madewithtauri.com/submissions/habit-watcher#:~:text=Description.%20%22Habit%20Watcher%20is%20a%20simple%20habit,track%20your%20habits%20with%20Github%2Dlike%20contributions%20graph%22)
[7] [https://github.com](https://github.com/coleam00/habit-tracker)
[8] [https://github.com](https://github.com/jofoerster/habitsync)
[9] [https://stackoverflow.com](https://stackoverflow.com/questions/54693223/what-does-yarn-build-command-do-are-npm-build-and-yarn-build-similar)
[10] [https://github.com](https://github.com/henry-azer/habit-it-app#:~:text=How%20to%20Use%20*%20Open%20Android%20Studio,the%20console%20to%20get%20the%20required%20dependencies:)
