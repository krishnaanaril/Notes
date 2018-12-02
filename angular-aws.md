# Deploying Angular PWA in AWS

* First create an angular app using `@angluar/cli`
* Configure aws amplify
* Add storage by : 
``` amplify add storage``` which will create an S3 bucket.
* Our angular build files will be copied to this S3 bucket.
* My deploy command is as follows: 
> ng build --prod
> 
> aws s3 cp dist/zettle/ s3://zettle96c8102a10ad40f38724d80d4dd72811/ --recursive --acl public-read
* Got S3 bucket settings and enable static site hosting with index.html as index document.
* Now the site will be available at `http://<bucket-name>.s3-website-<region>.amazonaws.com`, but the routing won't work.
* For routing to work, we need aws cloudfront. Got to aws cloudfront and create a new distribution.
* Origin domain should be the one url mentioned above.
* If we do not have any subfolders orgin path should be empty. Rest of the things are default.
* Add two error pages for 400 and 403 to reroute to index.html. Now angular routing should work.