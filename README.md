# Bulletproof Design Stack Protocol
*Written by James Mackenzie For Bulletproof Design Stack Capabilities*

1. [Set up Permissions](#requiredPermissions)
2. [Create Next.js App](#createApp)
3. [Use Unframer](#unframer)
4. [Deploy App](#deploy)
   1. [Push Changes](#push)
   2. [Publish via Vercel](#publish)
   3. [Pull Changes](#pull)
   4. [Create Branch](#branch)
   3. [Clone App](#clone)

## <a name="requiredPermissions">Required Permissions</a>
1. Xcode License
    1. Download [here](https://developer.apple.com/xcode/)
    2. Accept terms and conditions with administrative password
2. Node.js *(npm)*
    1. Download [here](https://nodejs.org/en/download/prebuilt-installer)
    2. Accept terms and conditions with administrative password
3. Github account and personal access token
    1. Login [here](https://github.com/)
    2. Go to Account Settings / Developer Settings / Personal Access Tokens / Generate new token
4. Vercel account
    1. Create account [here](https://vercel.com/signup) with Github login


## <a name="createApp">Create Next.js App</a>
For more details, see next.js documentation [here](https://nextjs.org/learn-pages-router/basics/create-nextjs-app/setup).
### Initialise App

1. **Set up** app by opening a new window in VSCode at the current working directory to the location where you want the app to live
2. Run the following command in the terminal and accept the default settings.

    ```
    npx create-next-app@latest [PROJECT-NAME] --use-npm
    ```

2. **Run on local server** on localhost

   ```    
    cd [PROJECT-NAME]
    npm run dev
    ```
   If you are using a React app, use ```npm start``` to run localhost server.
    
3. **Close local server** and return to local directory terminal

   ```    
   control-C
   ```

## <a name="unframer">Use Unframer</a>
For more details, see unframer documentation [here](https://github.com/remorses/unframer/tree/main).


1. Install the package
    ```
    npm install unframer
    ```
2. Map framer-motion to unframer
    ```
    npm install framer-motion@npm:unframer
    ```
3. Create an ```unframer.config.json``` file like the following within src/app.
    
    ```json
    {
    "$schema": "https://unframer-schema.vercel.app/schema.json",
    "outDir": "./framer",
    "breakpoints": { "sm": 300, "md": 760 },
    "components": {
        "headings": "https://framer.com/m/Headings-74WU.js",
        "navbar": "https://framer.com/m/Navbar-yGyf.js"
     }
    }
    ```

4. Copy your framer component url and add it to your config (remove the part after @ to always use the latest version)

5. Move terminal directory to ```app``` (where ```unframer.config.json``` is)

    ```
    cd src
    cd app
    ```

6. Run unframer command
    ```
    npx unframer
    ```
7. Import the componenent and stylesheet inside your ```jsx``` files, for example
    ```js
    import './framer/styles.css'. // load base Framer styles
    import Menu from './framer/menus'

    export default function App() {
    return (
        <div>
            <Menu componentVariable='some variable' />
        </div>
     )
    }
    ```
    
**Responsive and styled variants** can be used like this
   ```js
    import './framer/styles.css'
    import Logos from './framer/logos'

    export default function App() {
    return (
        <div>
            {/* Changes component variant based on breakpoint */}
            <Logos.Responsive
                variants={{
                    lg: 'Desktop Variant',
                    md: 'Tablet Variant',
                    base: 'Mobile Variant',
                }}
                style={{width:"100vh"}}
            />
        </div>
     )
   }
   ```
   
**Update unframer components** as above
1. Move terminal directory to ```app``` (where ```unframer.config.json``` is)
   ```
   cd src
   cd app
   ```
2. Run unframer command
   ```
   npx unframer
   ```


## <a name="deploy">Deploy App</a>
**Create and Push to Github Repository**
1. Login to your Github account
2. Click on the "+" icon at the top right corner and select "New repository"
2. Add the [PROJECT-NAME], and click "Create repository".
3. Github will return similar code to this which will be created unique for your new repository, copy it

```
echo "# [PROJECT-NAME]" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/[ACCOUNT-NAME]/[PROJECT-NAME].git
git push -u origin main
```
4. Paste your copied code **into the project local directory terminal**, not ```app/src```

### <a name="push">Push Changes</a>

1. ```git add .``` Collect all the changes from the code.
2. ```git commit -m 'message'``` Commit changes to GitHub with a clear message describing what they are.
3. ```git push origin main``` Push changes to the main branch.

## <a name="publish">Publish via Vercel</a>
1. Login to Vercel
2. Import your github repo from [here](https://vercel.com/import/git) (https://vercel.com/import/git).
2. You should be deployed!

### <a name="pull">Pull Changes</a>

1. ```git status``` to check which branch you are in.
2. ```git checkout main``` to move to main/any relevant branch.
3. ```git pull``` to update your local code.


### <a name="branch">Create Branch</a>
1. ```git branch new-branch-name``` to create 'new-branch-name'.
2. ```git checkout new-branch-name``` to move git location to new branch.
3. Push & pull changes as above replacing ```main``` with your ```new-branch-name```.
4. Review and merge branch in your github account.


### <a name="clone">Clone App</a>

1. On GitHub.com, navigate to the main page of the repository.

2. Above the list of files, click  Code.

3. Copy the URL for the repository under HTTPS
4. Open Terminal at the current working directory to the location where you want the cloned directory

4. Type ```git clone```, and then paste the URL you copied earlier.
    
    ```
    git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
    
5. Press Enter to create your local clone

6. Push/pull changes to the main branch as above


