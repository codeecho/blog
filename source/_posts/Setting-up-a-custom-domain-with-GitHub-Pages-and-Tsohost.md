title: "Setting up a custom domain with GitHub Pages and Tsohost"
date: 2015-06-12 11:58:28
tags:
- GitHub
- Tsohost
- DevOps
categories:
- How To
---
Setting up a custom domain for GitHub pages is pretty straightforward, but there is an added wrinkle when using Tsohost which isn't immediately obvious and cost me a nearly a week trying to solve it.

### Add a CNAME file to your Github repository
The first thing you need to do is add a CNAME file to your Github repository. This must go in the root of your repository and the filename but be uppercase. This file must contain the custom domain to your repository's root directory. For more information, see ["Adding a CNAME file to your repository."](https://help.github.com/articles/adding-a-cname-file-to-your-repository)

### Configure your Tsohost DNS settings
Login to Tsohost, select My Domains>Custom DNS from the right hand menu, and select the domain you want to setup from the drop down.

To configure a subdomain (eg. www) to point to your GitHub Pages, add a new entry of type "CNAME". Under the "Content" column add the url of your Github pages eg. "codeecho.github.io". For more information, see ["Tips for configuring a CNAME record with your DNS provider."](https://help.github.com/articles/tips-for-configuring-a-cname-record-with-your-dns-provider)

To configure the apex domain (the raw domain without any subdomain eg. codeecho.co.uk) to point to your GitHub Pages you will need to add 2 new entries of type "A" with "Content" values "192.30.252.153" and "192.30.252.154". For more information, see ["Tips for configuring an A record with your DNS provider."](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider)

### Update your Tsohost Nameservers
This is the bit that I missed even though it tells you to do it on the page when editting your DNS settings, but who reads all that stuff.
By default the Tsohost Nameservers are set to "ns1.tsohost.co.uk" and "ns2.tsohost.co.uk" which assumes that the site you wish to serve is hosted by Tsohost. To use an external host such as Github Pages you need to set these values to "ns1.tsodns.com" and "ns2.tsodns.com".

### And wait...
After you've completed all of the above you'll have to wait for these changes to propogate. This can take up to a day, so be patient.
