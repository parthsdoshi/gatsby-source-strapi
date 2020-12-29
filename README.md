# gatsby-source-strapi

Forked from the original because the original doesn't have a release with the latest master (at time of writing 2020-11-17)
Thus, I wanted to point yarn to install the latest master but there's no "prepare" script in the actual `gatsby-source-strapi` repo.
Due to the above, I forked it and added a "prepare" script to the package's "package.json".

Now, I can point yarn to install this as "gatsby-source-strapi" and get the "latest" master's features which is adding dynamic zone support.

> **WARNING**: This is the README for v1.0.0-alpha.0 make sure to install it with @alpha to try it out

## Install

`npm install --save gatsby-source-strapi@alpha`

## How to use

```javascript
// In your gatsby-config.js
plugins: [
  {
    resolve: `gatsby-source-strapi`,
    options: {
      apiURL: `http://localhost:1337`,
      queryLimit: 1000, // Default to 100
      contentTypes: [
        `article`,
        `user`,
        // if you don't want to leave the definition of an api endpoint to the pluralize module
        {
          name: `collection-name`,
          endpoint: `custom-endpoint`,
        },
      ],
      //If using single types place them in this array.
      singleTypes: [`home-page`, `contact`],
      // Possibility to login with a strapi user, when content types are not publically available (optional).
      loginData: {
        identifier: '',
        password: '',
      },
    },
  },
];
```

## How to query

You can query Document nodes created from your Strapi API like the following:

```graphql
{
  allStrapiArticle {
    edges {
      node {
        id
        title
        content
      }
    }
  }
}
```

To query images you can do the following:

```graphql
{
  allStrapiArticle {
    edges {
      node {
        id
        singleImage {
          localFile {
            publicURL
          }
        }
        multipleImages {
          localFile {
            publicURL
          }
        }
      }
    }
  }
}
```
