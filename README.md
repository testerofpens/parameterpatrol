# ParameterPatrol

A python project for searching archive.org and recording parameters within forms and urls. 
The results can then be compared to the current version of the web site, any differences can be investigated to see if the current site accepts old/dormant parameters which could be vulnerable to security issues such as SQLi, XSS, Authenication Bypasses, etc.
Currently, results are saved to a sqlite database in the current working directory.
The next version will include comparison funtionality between archived results.


## Usage Examples
Search archive.org for the target domain and include any additional domains listed using the -i option. Since no search year has been provided, interactive mode will be started to help choose an archived year.

```
  parameterpatrol -t http://www.example.com -i example.com,dev.example.com

  paramterpatrol -s http://localhost:8000

  paramterpatrol -s http://uat.example.com
```  

## Arguments for Searching Archive.org
  -t or --target= (mandatory): Specify the target domain to search for on archive.org. Note: http:// or https:// scheme values should be supplied.\n' 

  -i or --includedomain= (optional): Specify a list of additional domains to include in the crawler. If ommited, searches will only  be performed against the target domain. 
   For example, if "www.example.com" is the target domain, "example.com" or "dev.example.com" would not be included unless specified using the "-i" option. This option may be a single domain or a comma seperated list (no spaces). Note: a list of domains which have been excluded by the cralwer are logged in a file named "uncrawled_domains.log". 
   If you wish to include an ommited domain, re-run the search again, supplying the domain in the "-i" argument list. This option should only be used for related domains e.g. sub-domains like dev.example.com. Listing a third party domain such as anotherexample.com will only cause the crawler to crawl the third party site and cause unnecessary delays.


## Arguments for Searching Other Locations
  -s or --site= (mandatory): Specify the name of the site to search which is not located on archive.org. This option can be used to generate results of a current site for later comparison against archive.org results or comparison against an older archive of the site from a previous penetration test. 
  Note: http:// or https:// scheme values should be supplied.


