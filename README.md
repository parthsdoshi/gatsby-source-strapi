# gatsby-source-strapi

Forked from the original because the original doesn't have a release with the latest master (at time of writing 2020-11-17)
Thus, I wanted to point yarn to install the latest master but there's no "prepare" script in the actual `gatsby-source-strapi` repo.
Due to the above, I forked it and added a "prepare" script to the package's "package.json".

Now, I can point yarn to install this as "gatsby-source-strapi" and get the "latest" master's features which is adding dynamic zone support.
