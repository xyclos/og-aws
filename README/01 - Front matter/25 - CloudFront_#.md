#CloudFront
----------

### CloudFront Basics

-	📒 [Homepage](https://aws.amazon.com/cloudfront/) ∙ [Developer guide](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/) ∙ [FAQ](https://aws.amazon.com/cloudfront/faqs/) ∙ [Pricing](https://aws.amazon.com/cloudfront/pricing/)
-	**CloudFront** is AWS’ [content delivery network (CDN)](https://en.wikipedia.org/wiki/Content_delivery_network).
-	Its primary use is improving latency for end users in to accessing cacheable content by hosting it at [over 60 global edge locations](http://aws.amazon.com/cloudfront/details/).

### CloudFront Alternatives and Lock-in

-	🚪CDNs are [a highly fragmented market](https://www.datanyze.com/market-share/cdn/). CloudFront has grown to be a leader, but many alternatives that might better suit specific needs.

### CloudFront Tips
-	🐥**IPv6** is [now supported](https://aws.amazon.com/about-aws/whats-new/2016/10/ipv6-support-for-cloudfront-waf-and-s3-transfer-acceleration/)!
-	🐥**HTTP/2** is [now supported](https://aws.amazon.com/about-aws/whats-new/2016/09/amazon-cloudfront-now-supports-http2/)! Clients [must support TLS 1.2 and SNI](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesSupportedHTTPVersions).
-	While the most common use is for users to browse and download content (GET or HEAD methods) requests, CloudFront also supports ([since 2013](https://aws.amazon.com/blogs/aws/amazon-cloudfront-content-uploads-post-put-other-methods/)) uploaded data (POST, PUT, DELETE, OPTIONS, and PATCH).
	-	You must enable this by specifying the [allowed HTTP methods](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesAllowedHTTPMethods) when you create the distribution.
	-	Interestingly, the cost of accepting (uploaded) data [is usually less](https://aws.amazon.com/cloudfront/pricing/) than for sending (downloaded) data.
-	In its basic version, CloudFront [supports SSL](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecureConnections.html) via the [SNI extension to TLS](https://en.wikipedia.org/wiki/Server_Name_Indication), which is supported by all modern web browsers. If you need to support older browsers, you need to pay a few hundred dollars a month for dedicated IPs.
	-	💸⏱Consider invalidation needs carefully. CloudFront [does support invalidation](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html) of objects from edge locations, but this typically takes many minutes to propagate to edge locations, and costs $0.005 per request after the first 1000 requests. (Some other CDNs support this better.)
-	Everyone should use TLS nowadays if possible. [Ilya Grigorik’s table](https://istlsfastyet.com/#cdn-paas) offers a good summary of features regarding TLS performance features of CloudFront.
-	An alternative to invalidation that is often easier to manage, and instant, is to configure the distribution to [cache with query strings](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/QueryStringParameters.html) and then append unique query strings with versions onto assets that are updated frequently.
-	⏱For good web performance, it’s important turn on the option to [enable compression](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ServingCompressedFiles.html) on CloudFront distributions if the origin is S3 or another source that does not already compress.

### CloudFront Gotchas and Limitations

-	If using S3 as a backing store, remember that the endpoints for website hosting and for general S3 are different. Example: “bucketname.s3.amazonaws.com” is a standard S3 serving endpoint, but to have redirect and error page support, you need to use the website hosting endpoint listed for that bucket, e.g. “bucketname.s3-website-us-east-1.amazonaws.com” (or the appropriate region).
-   🔸By default, CloudFront will not forward HTTP Host: headers through to your origin servers. This can be problematic for your origin if you run multiple sites switched with host headers. You can [enable host header forwarding](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/RequestAndResponseBehaviorCustomOrigin.html#request-custom-headers-behavior) in the default cache behavior settings.

