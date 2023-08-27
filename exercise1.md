# Git Exercise 1
## Pushing and Pulling - The Basics

In this exercise, you will learn the following:

- How to sign up to a based online product (we will use Github ) ✔
- Installing Git on your machine ✔
- Set your name and email in Git ✔
- Enable storing your git credentials ✔
- Creating a git repo ✔
- Cloning it locally
- Creating branches
- Deleting Branches
- Listing Branches (local)
- Listing Branches (remote)
- Making changes: add (stage) / commit / push
- Pulling changes: fetch + merge _versus_ pull
- Using git diff
- Seeing your commit history

### 1. How to sign up to a based online product (we will use Github )
- Go to the GitHub website and sign up to get an account. Make a note of your account details
- Setup your personal access token (tick all the permissions). Make a note of this, you won't see it again once you leave this screen. 
- _Tip:_ you can find this in Developer Options and we cover this in the video. I use the classic personal access token. Set the expiration to _never expires_ or maximum amount of days available.

### 2. Installing Git on your machine
- You can figure this out yourself. If you're using mac, you can use brew, or just google 'how to install git on macos'. If you're on Windows, you can use an .exe file which you can find online.
- Test the installation by going to your cli / terminal / command line, and type 'git'. This should yield the full list of options you have available in a list.

### 3. Set your name and email in Git
- When you make commits, it helps to know who made the commit and what their email is. Rather than use your default credentials from github account, OR defaulting to your login name etc, we will store a set name and email in the **- - global config**. 

```
git config --global user.name "Mary Jane"
git config --global user.email "mary.jane@example.com"
```

### 4. Enable storing your git credentials
- When we have a remote (GitHub) hosted git repository, they are often private and changes require having credentials. Even public repositories require credentials by the owner to change contents and add / remove files to the repo
- Often when we do a `git push`, we have to log-in to GitHub. To avoid logging in repeatedly, you can enable storage of credentials which will ensure you don't have to keep logging in
- With this option, **you** have to be aware that git stores the credentials in a plain text file, which can be exploited by malicious third-party code or others who may have acess to your machine
- Finally, with this option, if your login is _unsuccessful_ then your git pull / push will fail, which will **remove the stale (current) credential from the store**, and successful future login credentials will then subsequently be stored.
- simply run:
```
git config --global credential.helper store
```

### 5. Creating a git repo
- Create a _private_ git repo in GitHub called 'myfirstrepo'
- Go through the options and allow it to create a default 'main' branch with a ReadMe.md tile to begin with

### 6. Cloning it locally
- Go on to the 'myfirstrepo' GitHub page which should be defaulted to the _main_ branch view. There's a green button called '<>Code'. Click on that - it's a drop-down. Under **clone**, copy the 'HTTPS uri
- Go back to your local machine's terminal, and create a new directory called 'repos' e.g. `mkdir ~/repos` (`~` is linux speech for _my home directory_, but this is not a Linux course!)
- Go into the repos directory e.g. `cd repos` (`cd` is linux speech for _change my directory to_)
- Once inside the repos directory run the following with your https uri copied above:
`git clone https://github.com/yourpathhere`
- This will now download your GitHub repo and its content in a **local repo** and manage link it to the **remote repo**, where you will be able to run git commands and manage the contents here
- 

Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
