<!-- AUTO-GENERATED-CONTENT:START (STARTER) -->


<h4 align="left">Home</h4>
<p align="center">
  <img alt="home" src = "https://github.com/CodeChef7/jobboard/src/assets/images/jobboard.png">


<h1 align="center">
  job board
</h1>

<br/>
  jobboard is an  created by CodeChef7.ai to allow developers to build easily AI powered job listing platforms and job matching applications.
<br/>

## About CodeChef7.ai
  https://www.CodeChef7.ai is an API first company that provides the most sophisticated AI Powered JOB & PROFILE API. Corporates and Software vendors can leverage our technology layers to Parse, Enrich and Score both job and candidate data. The platform supports +200 apps, pipelines and code integrations so you can automate workflows with your favorite tools.
  - Our Developers documentation : https://developers.CodeChef7.ai/
  - Our API list (Parsing, Revealing, Embedding, Searching, Scoring, Reasoning) : https://www.CodeChef7.ai/api
  - Our cool demos labs : https://labs.CodeChef7.ai

## 🙈 Demo of jobboard
  Vidéo demo: https://CodeChef7.wistia.com/medias/gvf4u3fe48
  <br/>
  <br/>
  ![alt text](https://s3.amazonaws.com/img.CodeChef7.net/Screen+Shot+2020-12-12+at+23.11.00.png)


## 🚀 Quick start

1.  **Clone this repository.**

  ```shell
  git clone  https://github.com/CodeChef7/jobboard.git
  ```

2.  **Start developing.**

  Navigate into your new site’s directory and start it up.

  ```shell
  cd jobboard/
  npm install
  npm start
  ```

3.  **Add environment variables**

  The project environment variables must be  defined in the **.env.developement** and **.env.production** files in the root directory of the project.

  > Please note that you shouldn’t commit .env.* files to your source control and rather use options given by your Continuous Deployment (CD) provider.
  An example is Netlify with its [build environment variables](https://www.netlify.com/docs/continuous-deployment/#build-environment-variables).

  Here is an exemple of the .env files:

  - .env.development
  ```
    API_URL=https://api.CodeChef7.ai/v1
    API_KEY=Your team api key
    BOARD_KEYS=Your team list of board keys for development
    SOURCE_KEY=Your team source key for development
    AGENT_KEY=Your team agent key for development
    GOOGLE_API_KEY=Your google api key (used for places searching)
  ```
  - .env.production
  ```
    API_URL=https://api.CodeChef7.ai/v1
    API_KEY=Your team api key
    BOARD_KEYS=Your team list of board keys for production
    SOURCE_KEY=Your team source key for production
    AGENT_KEY=Your team agent key for production
    GOOGLE_API_KEY=Your google api key (used for places searching)
  ```

  4.  **jobboard code and start editing!**

    Your site is now running at `http://localhost:8000`!


## :wrench: Configure and customize the job board

1. **Colors and images:**

  The project uses sass preprocessor for css, the variables and mixing are defined in **src/styles/helpers.scss**.
  You can change the images and logos directly in the **src/assets** directory.

2. **Website metadata, information, SEO and description:**
  This project uses the react helmet pluging that provides drop-in support for server side rendering, and let you control your document head using a simple react component

  with this plugings you can add attributes like website title, meta attributes, description, etc... and will get added to the static html build.
  
  This attributes can be added to the file **gatsby-config.js**

  ```javascript
  module.exports = {
    siteMetadata: {
      title: 'Your job board title',
      description: `
        Your job board description
      `,
      siteUrl: 'https://example.com',
      image: 'your og image url',
      author:  'CodeChef7.ai',
      organization: {
        name: 'CodeChef7.ai',
        url: 'https://CodeChef7.ai',
        logo: 'https://img.CodeChef7.net/logo/Logo.svg',
      },
    },
    plugins: [
      'gatsby-plugin-sass',
      '@bumped-inc/gatsby-plugin-optional-chaining',
      `gatsby-plugin-react-helmet`,
      'gatsby-plugin-root-import',
      {
        resolve: `gatsby-plugin-s3`,
        options: {
          bucketName: "your s3 bucket name",
        },
      },
    ],
  }
  ```

  And you can personalize the attributes to be added to the head of each page by editing the component **src/components/seo**

  ```javascript
  import React from "react"
  import PropTypes from "prop-types"
  import { Helmet } from "react-helmet"
  import { useStaticQuery, graphql } from "gatsby"

  function SEO({ description, lang, meta, title }) {
    const { site } = useStaticQuery(
      graphql`
        query {
          site {
            siteMetadata {
              title
              description
              author
              organization {
                name
                url
                logo
              }
            }
          }
        }
      `
    )

    const metaDescription = description || site.siteMetadata.description

    return (
      <Helmet
        htmlAttributes={{
          lang,
        }}
        title={title}
        titleTemplate={`%s | ${site.siteMetadata.title}`}
        meta={[
          {
            name: `description`,
            content: metaDescription,
          },
          {
            property: `og:title`,
            content: title,
          },
          {
            property: `og:description`,
            content: metaDescription,
          },
          {
            property: `og:type`,
            content: `website`,
          },
          {
            name: `twitter:card`,
            content: `summary`,
          },
          {
            name: `twitter:creator`,
            content: site.siteMetadata.author,
          },
          {
            name: `twitter:title`,
            content: title,
          },
          {
            name: `twitter:description`,
            content: metaDescription,
          },
          {
            name: `organization`,
            content: site.siteMetadata.organization.name,
          },
          {
            name: `organization url`,
            content: site.siteMetadata.organization.url,
          },
          {
            name: `organization logo`,
            content: site.siteMetadata.organization.logo,
          },
        ].concat(meta)}
      />
    )
  }

  SEO.defaultProps = {
    lang: `en`,
    meta: [],
    description: ``,
  }

  SEO.propTypes = {
    description: PropTypes.string,
    lang: PropTypes.string,
    meta: PropTypes.arrayOf(PropTypes.object),
    title: PropTypes.string.isRequired,
  }
  export default SEO
  ```


## 🧐 What's inside?

  A quick look at the top-level files and directories you'll see in a Gatsby project.

    .
    ├── node_modules
    ├── src
    │   ├── assets 
    │   ├── components
    │   ├── hooks
    │   ├── pages
    │   ├── store
    │   ├── styles
    │   └── utiles  
    ├── .gitignore
    ├── .prettierrc
    ├── gatsby-browser.js
    ├── gatsby-config.js
    ├── gatsby-node.js
    ├── gatsby-ssr.js
    ├── LICENSE
    ├── package-lock.json
    ├── package.json
    └── README.md

  1.  **`/node_modules`**: This directory contains all of the modules of code that your project depends on (npm packages) are automatically installed.

  2.  **`/src`**: This directory will contain all of the code related to what you will see on the front-end of your site (what you see in the browser) such as your site header or a page template. `src` is a convention for “source code”.

      This directory contains:  
        >**`assets`** All your assets files like images, fonts, icons... goes here.  
        >**`components`** Contains all the app functional components.  
        >**`hooks`** Contains some custom hooks.  
        >**`pages`** Contains the app main containers (website pages).  
        >**`store`** Contains actions and reducers of our app, it holds the whole state tree of your application. The only way to change the state inside it is to dispatch an action on it.  
        >**`utils`** Contains app configuration and utilities.  

  3.  **`.gitignore`**: This file tells git which files it should not track / not maintain a version history for.

  4.  **`.prettierrc`**: This is a configuration file for [Prettier](https://prettier.io/). Prettier is a tool to help keep the formatting of your code consistent.

  5.  **`gatsby-browser.js`**: This file is where Gatsby expects to find any usage of the [Gatsby browser APIs](https://www.gatsbyjs.org/docs/browser-apis/) (if any). These allow customization/extension of default Gatsby settings affecting the browser.

  6.  **`gatsby-config.js`**: This is the main configuration file for a Gatsby site. This is where you can specify information about your site (metadata) like the site title and description, which Gatsby plugins you’d like to include, etc. (Check out the [config docs](https://www.gatsbyjs.org/docs/gatsby-config/) for more detail).

  7.  **`gatsby-node.js`**: This file is where Gatsby expects to find any usage of the [Gatsby Node APIs](https://www.gatsbyjs.org/docs/node-apis/) (if any). These allow customization/extension of default Gatsby settings affecting pieces of the site build process.

  8.  **`gatsby-ssr.js`**: This file is where Gatsby expects to find any usage of the [Gatsby server-side rendering APIs](https://www.gatsbyjs.org/docs/ssr-apis/) (if any). These allow customization of default Gatsby settings affecting server-side rendering.

  9.  **`LICENSE`**: This Gatsby starter is licensed under the 0BSD license. This means that you can see this file as a placeholder and replace it with your own license.

  10. **`package-lock.json`** (See `package.json` below, first). This is an automatically generated file based on the exact versions of your npm dependencies that were installed for your project. **(You won’t change this file directly).**

  11. **`package.json`**: A manifest file for Node.js projects, which includes things like metadata (the project’s name, author, etc). This manifest is how npm knows which packages to install for your project.

  12. **`README.md`**: A text file containing useful reference information about this project.


## 💫 Deploy
  The project is pre-configured to be deployed to aws s3, you just need to add and configure your aws cridentials using aws-cli locally.
  And run the following command:  

  ```shell
  npm run build
  npm run deploy
  ```

  Otherwise you can take a look on this alternatives:  

  [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/gatsbyjs/gatsby-starter-hello-world)  
  [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/gatsbyjs/gatsby-starter-hello-world) 


## :octocat: Contributions

  Please feel free to contribute to the quality of this content by submitting PRs for improvements to code, architecture, etc. While typo fixes are welcomed, they will likely be caught through normal editing/publishing processes, so please don't worry about them right now.

  Any contributions you make to this effort are of course greatly appreciated.

<!-- AUTO-GENERATED-CONTENT:END -->
