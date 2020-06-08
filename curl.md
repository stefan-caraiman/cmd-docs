# curl

issue a GET request to a URL
    curl http://www.example.com

issue a PUT request with a JSON payload
    curl -X PUT http://www.example.com -d '{"key": "value"}'

POST data.txt to a URL
    curl -X POST http://www.example.com --data-binary @data.txt

issue a GET request with a header Key paired to Value
    curl -X PUT http://www.example.com -H "Key:Value"


# Basic Usage

Issue an HTTP request of a particular method type to a URL. By default `curl`
issues a GET request. The `-X` flag lets you specify other methods, like PUT
and POST:
    curl -X <method> <url>


# Cookies

`curl` can use cookies. The `--cookie` flag allows you to set name=value pairs
at the command line. This command will issue a GET request, print verbose
output (`-v`), and pass a cookie where TOKEN is set to data
(`--cookie "TOKEN=data"`):
    curl -v --cookie "TOKEN=data" http://www.example.com

# Querying Sets and Ranges

`curl` can be used to issue requests to numerous URLs simultaneously, issued in
sequential order. This command will issue requests to both the www and admin
subdomains (`{www,admin}`) of example.com:
    curl http://{www,admin}.example.com

It can also query sequential ranges by placing numbers in square brackets. This
will issue requests for resources 1.txt, 2.txt, 3.txt, and 4.txt (`[1:4]`) from
example.com:
    curl http://www.example.com/[1:4].txt

You can also specify a step. This will query letters of the alphabet (`a-z`),
but only every second letter (`:2`):
    curl http://www.example.com?letter=[a-z:2]

# curl                                                                                        
                                                                                              
  Transfers data from or to a server.                                                         
  Supports most protocols, including HTTP, FTP, and POP3.                                     
  More information: <https://curl.haxx.se>.                                                   
                                                                                              
- Download the contents of an URL to a file:                                                  
                                                                                              
  curl http://example.com -o filename                                                         
                                                                                              
- Download a file, saving the output under the filename indicated by the URL:                 
                                                                                              
  curl -O http://example.com/filename                                                         
                                                                                              
- Download a file, following [L]ocation redirects, and automatically [C]ontinuing (resuming) a previous file transfer:
                                                                                              
  curl -O -L -C - http://example.com/filename                                                 
                                                                                              
- Send form-encoded data (POST request of type `application/x-www-form-urlencoded`):          
                                                                                              
  curl -d 'name=bob' http://example.com/form                                                  
                                                                                              
- Send a request with an extra header, using a custom HTTP method:                            
                                                                                              
  curl -H 'X-My-Header: 123' -X PUT http://example.com                                        
                                                                                              
- Send data in JSON format, specifying the appropriate content-type header:                   
                                                                                              
  curl -d '{"name":"bob"}' -H 'Content-Type: application/json' http://example.com/users/1234  
                                                                                              
- Pass a user name and password for server authentication:                                    
                                                                                              
  curl -u myusername:mypassword http://example.com                                            
                                                                                              
- Pass client certificate and key for a resource, skipping certificate validation:            
                                                                                              
  curl --cert client.pem --key key.pem --insecure https://example.com                         
                                                                                              
                                                                                              
                                                                                              
# To download a file:
curl <url>

# To download and rename a file:
curl <url> -o <outfile>

# To download multiple files:
curl -O <url> -O <url>

# To download all sequentially numbered files (1-24):
curl http://example.com/pic[1-24].jpg

# To download a file and pass HTTP authentication:
curl -u <username>:<password> <url>

# To download a file with a proxy:
curl -x <proxy-host>:<port> <url>

# To download a file over FTP:
curl -u <username>:<password> -O ftp://example.com/pub/file.zip

# To get an FTP directory listing:
curl ftp://username:password@example.com

# To resume a previously failed download:
curl -C - -o <partial-file> <url>

# To fetch only the HTTP headers from a response:
curl -I <url>

# To fetch your external IP and network info as JSON:
curl http://ifconfig.me/all.json

# To limit the rate of a download:
curl --limit-rate 1000B -O <outfile>

# To get your global IP:
curl httpbin.org/ip 

# To get only the HTTP status code:
curl -o /dev/null -w '%{http_code}\n' -s -I URL
