# GitHub Codespaces ♥️ Port Forwarding

This is a GitHub Codespace that shows how port forwarding works within Codespaces. Please check out this blog post for more details: https://dev.to/github/share-your-locally-hosted-web-app-using-codespaces-276k

One of my favorite things about GitHub Codespaces is that it makes pair programming easier. As the software engineering industry shifted from in-person to remote work, we've learned how to prioritize a seamless developer experience for virtual collaboration.

When I worked in a physical office, pair programming consisted of sitting next to a fellow software engineer and staring at a computer screen together. We could look at the code editor, console, and browser to debug. Virtual work presented a challenge: how do we share screens and keyboards (typing) even though we weren't in the same room? Fortunately, products like Zoom, Slack, and the Visual Studio Code Live Share extension improved, enabling us to code better together. 

For many reasons, GitHub Codespaces quickly made its way to my list of helpful tools for remote code collaboration. One of the many reasons is that it enables developers to share their locally hosted web applications through port forwarding.

In this post, I'll walk you through how to share your locally hosted web app using GitHub Codespaces. 

## What is GitHub Codespaces?
GitHub Codespaces is a cloud-based development environment that enables developers to code from anywhere, a.k.a. you can use GitHub Codespaces to code in your browser. It's a fully-decked-out code editor in your browser. As long as you have internet, you can write and read code from any device, including an iPad. 

## Who has access to GitHub Codespaces?
Every GitHub users have free access to 60 hours of GitHub Codespaces a month, and you can upgrade to a paid plan if you need more hours.

![Codespaces available for all users. 60 hours of free usage every month](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wfj5s177t9dj35c53v71.jpeg)

## What is port forwarding?
Port forwarding redirects network traffic from one port to another port that lives on the same computer or a different computer. In Codespaces, you can run a web app on a particular port, then forward the port to your local machine so you can test and debug. The best part is you can share your port with necessary teammates and collaborators so that they can view your locally hosted web application. 

## How to share your locally hosted web app using GitHub Codespaces
Let's try out sharing a locally hosted web app using GitHub Codespaces! 

### Step 1: Create a Codespaces instance (or a Codespaces template)
You can start a new Codespaces instance by creating a GitHub repository, choosing the Codespaces tab, and clicking the "New codespace" button. Then you can add a few lines of code that you'd like to run. OR, you can use a Codespaces template, which is faster, more exciting, and includes an already-running web app.

#### Create a Codespaces template
If you navigate to the URL https://github.com/codespaces/templates, you'll see a list of templates. You can choose a template that you'd like to use. For this example, I'll use the Next.js template. We'll see a few files inside this template, including a .devcontainer.json, components, and CSS. 

![a tiled list of Codespaces templates including Jupyter notebook, React, and Next.js](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/26xv6rdk5qhyvwfp1cbe.png)

### Step 2: Check out the .devcontainer.json file
As soon as you open the Next.js template, a browser tab opens up with a Next.js app. The devcontainer.json contains configurations that help us to immediately run the web app as soon as the Codespace builds.

In the devcontainer.json file, you'll see the following properties and commands that help the Codespaces instance run the web app immediately:
```
  "updateContentCommand": "npm install && npm run build",
  "postCreateCommand":"  ",
  "postAttachCommand": {
    "server": "npm run dev"
    }
```

These properties state that during and after the Codespaces build, it should run the above commands to install dependencies and run the web app.

The devcontainer.json file also contains a `forwardedPorts` property, which takes an array of ports that you'd like to forward. In the template, we're already forwarding port 3000. This tells Codespaces that we want to forward port 3000 to our local machine. 

```
"forwardedPorts": [
    3000
  ]
``` 

### Step 3: Check out the Simple Browser Tab

#### The simple browser tab already renders some code!
This template contains configurations to open a browser tab that renders our code. If you click on the Simple Browser tab, you'll see a Next.js app. You can make and view changes to the code in the `pages/index.js` file. Try changing the `<h1></h1>` element on line 31 to say, "Codespaces Port Forwarding Is Where It's At!" You will see the changes immediately reflected in the Simple Browser tab.  

#### The simple browser tab is already port forwarded!

You'll see a browser address bar with a URL in the Simple Browser tab. The URL will vary per person and project, but the general format is `https://<your-github-handle>-<a-codespaces-id-which-combines-a-words-and-random-characters>-<your-port-number>.preview.app.github.dev/`. For example, the URL could like `https://blackgirlbytes-unicorn-poop-5v123456789qvv-3000.preview.app.github.dev/`.

![](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jqmdce1yf8jcjikgaxff.png)

Codespaces forwarded port 3000 to this URL, so you can view your web app in the Simple Browser tab. You'll see the same web app if you go to the URL in a new tab (outside of Codespaces).

### Step 4: Share the URL 
You can now share your URL and make it available to your teammates or collaborators. Navigate to the ports tab (where your terminal typically lives), and you'll see a list of ports that you are forwarding. For each port, there is a:

- label column, 
- a local address column
- a running processes column
- a visibility column
- and an origin column


![listed ports with label column, local address, a running process, visibility, and origin column](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o1eckxdr2f3uhwoa1v9m.png)

If you right-click on the port you'd like to share, you'll see the option to switch the port visibility from "Private" to "Public." You can now copy the value in the local address and share it with necessary collaborators. Now, they can view your locally hosted web app and make more informed changes to the code. 

Bonus tip: if you create this Codespace instance under an organization, you can see three options for port visibility: "Private," "Public," and "Private to Organization." This is a great way to securely share your local web app, specifically with members of your organization.

![shows the option to make your port public](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/v7im8g7113kjjb0svb6a.png)

#### Labeling the port
If you have multiple ports running, it's helpful to label the port so that you can determine the difference between each port. To label a port, right-click on the port, and select "Label Port." Then, you can give the port a name that you can quickly identify.  


![shows developer labeling a port](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qczvgs1ffd8gigpy4zty.png)


**- If you're interested in learning more about GitHub Codespaces, check out the [GitHub Codespaces documentation](https://docs.github.com/en/codespaces).**

**- Follow [me](https://dev.to/blackgirlbytes) and [GitHub](https://dev.to/github) on Dev.to for more GitHub Codespaces tips and tricks!** 

**- You can also check out my [repository](https://github.com/blackgirlbytes/codespaces-forward-port) for reference.**

_Thanks for reading!_

To run this application:

```
npm run dev
```
