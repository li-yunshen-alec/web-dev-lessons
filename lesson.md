Tutorial by Alec

# Prerequisites

### Basic programming knowledge

We’re going to use JavaScript, but if you have knowledge of variables, functions, data types, Arrays and Objects, etc. in any language, you should be alright.

### Basic HTML

If you’ve used HTML before, you’re good to go.

# Development environment

### Node.js

This is your JavaScript runtime environment. Go here https://nodejs.org/en and install it if you haven’t already.

Next, verify that it works by opening a terminal and typing this command:

```bash
node -v
```

This should output the version of Node you just installed:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/db0f777b-a644-49ef-a40b-f9b5de98b062/Untitled.png)

If you see any errors, try reinstalling Node from the package you downloaded and retry the command again.

### **Visual Studio Code**

Visual Studio Code is a popular open-source IDE that works well for frontend development. There are a bunch of others you can try — see what your favourite is and download that if you prefer. For now, we'll run with VS Code.

Go here https://code.visualstudio.com/download and download it.

Follow the installation steps, and you should be good to go. Go ahead and fire up Visual Studio Code.

### Github

GitHub is a platform for version control and collaboration. It allows you to manage and store your code in repositories. To use GitHub, you'll need to create an account and install GitHub Desktop.

### Creating a GitHub Account

1. Go to https://github.com/join.
2. Fill out the form to create a new account.

### Installing GitHub Desktop

GitHub Desktop is a user-friendly application that simplifies the use of Git on your local machine.

1. Download GitHub Desktop from https://desktop.github.com/.
2. Install the application by following the instructions for your operating system.

### Setting Up GitHub Desktop

1. Open GitHub Desktop.
2. Sign in with your GitHub account.
3. You can now clone repositories, create new ones, and manage your code easily through the GitHub Desktop interface.

### Creating a New Repository with GitHub Desktop

1. Open GitHub Desktop.
2. Click on `File` > `New Repository...`.
3. Fill in the details for your new repository:
    - **Name**: Choose a name for your repository.
    - **Description**: Add a description (optional).
    - **Local Path**: Choose the location on your computer where you want to save the repository (optional).
4. Click `Create repository`.

### Opening the Repository in Visual Studio Code

1. Once the repository is created, go to GitHub Desktop.
2. Click on `Open in Visual Studio Code`.
3. Visual Studio Code will open with your newly created repository.

Now you have a new GitHub repository set up and opened in Visual Studio Code, ready for you to start coding!

# Setting Up a Project with React and Vite

Vite is a modern build tool that provides a fast and optimized development experience. We'll use it to set up a React project.

1. Open a terminal in Visual Studio Code. (Go to `Terminal` > `New Terminal` in your top navigation or do `Ctrl` + ``` on Windows)
2. You should already be inside your repository folder.
3. Run this command to create a project with Vite:

```bash
npm create vite@latest ./
```

1. When prompted to select a framework, select `React`.
2. Select `JavaScript + SWC` when prompted.
3. Go ahead and run these commands to install the necessary dependencies and run your project:

```bash
npm install
npm run dev
```

1. You should see an output like this. Go to [localhost:5173](http://localhost:5173) with your web browser of choice to see your project in action.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/4a8645ce-47b0-46cc-84ff-79a870b666ef/Untitled.png)

# Make your first changes

Go to `App.jsx`. You can see that the code in this file determines the HTML that you see on the main page, and the `.css` files around it determine the styles applied to it.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/3e14bea9-997f-4df8-b732-1ef2c6908e1f/Untitled.png)

Now delete all the code in App.jsx. We’re going to run the `rafce` command to automatically create the basis of our first component.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/54cbbdfb-d86c-41ce-9afc-74b70ac9e74f/Untitled.png)

For this command to work, go to `Extensions` in your sidebar, search for and install `ES7+ React/Redux/React-Native snippets`.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/22145ee1-c240-4404-8fa8-da7d014e93c5/Untitled.png)

What we have now is a JavaScript function that returns some HTML. Try changing the HTML, and you can see the website update as soon as you save.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/3528dd0d-bf0a-4c77-9d74-64070e634f15/Untitled.png)

Let’s try changing the JavaScript:

```jsx
import React from 'react'

const App = () => {
  const message = "This is my first variable rendered in JSX!";  

  const handleClick = () => {
		alert("you clicked the message!");
  }

  return (
    <div>
      <h1>Hello React World</h1>
      <h2 onClick={handleClick}>{message}</h2>
    </div>
  );
}

export default App
```

Since we’re basically just working with HTML inside JavaScript we can create and reference variables and functions outside of the return block.

# Creating a Multi-Page App with a Navbar

To create a multi-page app with a navigation bar, we will use React Router.

1. Open up a new terminal and install React Router DOM:

```bash
npm install react-router-dom
```

1. Create the necessary components for your pages. For example, create `Home.jsx`, `About.jsx`, and `Contact.jsx` in the `src/components` folder (you’ll have to make the components folder.) Run `rafce` to create your components quickly.

**src/components/Home.jsx**

```jsx
import React from 'react';

const Home = () => {
  return (
    <div>
      <h1>Home</h1>
    </div>
  );
};

export default Home;

```

**src/components/About.jsx**

```jsx
import React from 'react';

const About = () => {
  return (
    <div>
      <h1>About</h1>
    </div>
  );
};

export default About;

```

**src/components/Contact.jsx**

```jsx
import React from 'react';

const Contact = () => {
  return (
    <div>
      <h1>Contact</h1>
    </div>
  );
};

export default Contact;

```

1. Now update `App.jsx` to include the router and the navbar:

**src/App.jsx**

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';
import Home from './components/Home';
import About from './components/About';
import Contact from './components/Contact';

const App = () => {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/contact">Contact</Link>
            </li>
          </ul>
        </nav>

        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </div>
    </Router>
  );
};

export default App;
```

1. Save all your files to see your multi-page app in action.

You should now have a basic multi-page React application with a navigation bar, allowing you to navigate between the Home, About, and Contact pages.

# Troubleshooting

1. Go to https://github.com/li-yunshen-alec/new-project.
2. Clone the repository however you like. Open up the project in your code editor and open up a terminal in the project directory. Your screen should look almost exactly like this:

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/b05273ab-7d97-43eb-b3e5-5ae9043dc537/image.png)

1. Go ahead and run these commands to install the necessary dependencies and run your project:

```bash
npm install
```

```bash
npm run dev
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/4a8645ce-47b0-46cc-84ff-79a870b666ef/Untitled.png)

# Installing MantineUI

### What is it?

It’s a collection of reusable components that we’re going to use to build a functional site, fast.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/fa7b7ead-dd0d-44a3-9421-5341916aeed3/b3117925-0cbd-407e-a350-e93ce59ca3ac/image.png)

### How to install?

We’re just going to follow the steps from the official Mantine docs - for “Usage with Vite,” the React framework we’re using.

1. Install dependencies:

```bash
npm install @mantine/core @mantine/hooks
```

1. Install PostCSS things:

```bash
npm install --save-dev postcss postcss-preset-mantine postcss-simple-vars
```

1. Create a `postcss.config.cjs` file at the root of the application (same folder as `package.json`) with this content:

```json
module.exports = {
  plugins: {
    'postcss-preset-mantine': {},
    'postcss-simple-vars': {
      variables: {
        'mantine-breakpoint-xs': '36em',
        'mantine-breakpoint-sm': '48em',
        'mantine-breakpoint-md': '62em',
        'mantine-breakpoint-lg': '75em',
        'mantine-breakpoint-xl': '88em',
      },
    },
  },
};
```

1. Add styles imports and MantineProvider to your application root component (`App.jsx`):

```jsx
// Import styles of packages that you've installed.
// All packages except `@mantine/hooks` require styles imports
import '@mantine/core/styles.css';

import { MantineProvider } from '@mantine/core';

export default function App() {
  return <MantineProvider>{/* Your app here */}</MantineProvider>;
}
```