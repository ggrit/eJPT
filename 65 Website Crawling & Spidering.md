# 65 Website Crawling & Spidering

# Passive Crawling & Spidering with Burp Suite & OWASP ZAP

## Crawling

- Crawling is the process of navigating around the web application, following links, submitting forms and logging in (where possible) with the objective of mapping out and cataloging the web application and the navigational paths within it.
- Crawling is typically passive as engagement with the target is done via what publicly accessible, we can utilize Burp Suite's passive crawler to help us map out the web application to better understand how it is setup and how it works.


## Spidering

- Spidering is the process of automatically discovering new resources (URLs) on a web application/site.
- It typically begins with a list of target URLs called seeds, after which the Spider will visit the URLs and identified hyperlinks in the page and adds them to the list of URLs to visit and repeats the process recursively.
- Spidering can be quite loud and as a result, it is typically considered to be an active information gathering technique.
- We can utilize OWASP ZAP's Spider to automate the process of spidering a web application to map out the web application and learn more about how the site is laid out and how it works. 

#cybersecurity #eJPT 