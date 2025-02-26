# fuff
FFUF (Fuzz Faster U Fool) is a powerful web fuzzing tool that is included in Kali Linux. It is primarily used for discovering hidden directories and files on web servers through brute-forcing techniques.

### Installation

FFUF is typically pre-installed in Kali Linux. If it's not available, you can install it using:

```bash
sudo apt update
sudo apt install ffuf
```

### Basic Usage

The basic syntax for using FFUF is:

```bash
ffuf -u <url> -w <wordlist> -mc <status_code>
```

- `-u <url>`: The target URL with a placeholder for the fuzzing, e.g., `http://example.com/FUZZ`.
- `-w <wordlist>`: The path to the wordlist file you want to use for brute-forcing.
- `-mc <status_code>`: Specify which HTTP status codes to match (e.g., `200`, `403`).

### Examples

#### Example 1: Basic Directory Fuzzing

To perform a basic scan on a website to find hidden directories:

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -mc 200
```

**Expected Output:**

```
[STATUS CODE]
http://example.com/images (Status: 200)
http://example.com/css (Status: 200)
```

This output shows the found directories with their HTTP status codes.

#### Example 2: Fuzzing with a Custom Wordlist

You can use a custom wordlist to target specific directories or files:

```bash
ffuf -u http://example.com/FUZZ -w /path/to/custom_wordlist.txt -mc 200,403
```

**Expected Output:**

```
[STATUS CODE]
http://example.com/admin (Status: 200)
http://example.com/config.php (Status: 403)
```

This output displays both successful and forbidden responses.

#### Example 3: Fuzzing with Extensions

To search for files with specific extensions, you can include them in the wordlist or specify them in the command:

```bash
ffuf -u http://example.com/FUZZ.php -w /usr/share/wordlists/dirb/common.txt -mc 200
```

**Expected Output:**

```
[STATUS CODE]
http://example.com/index.php (Status: 200)
http://example.com/login.php (Status: 200)
```

#### Example 4: Recursive Fuzzing

To scan recursively, you can combine FFUF with recursive options or utilize multiple scans:

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -mc 200 -r
```

**Expected Output:**

```
[STATUS CODE]
http://example.com/admin (Status: 200)
http://example.com/admin/settings (Status: 200)
```

### Conclusion

FFUF is a versatile tool for discovering hidden files and directories on web servers. By utilizing different wordlists and options, you can tailor your scans for effective reconnaissance. Always ensure you have permission to scan the target website to avoid legal issues.



                                   ALTERNATIVE
Understood. Here is how to use the ffuf tool in Kali Linux, along with examples and expected outputs:

### What is ffuf?

ffuf (Fuzz Faster U Fool) is a fast web fuzzer written in Go. It is used to discover hidden web directories and files on a web server by brute-forcing URLs.

### Installation

ffuf is typically pre-installed in Kali Linux. If it's not installed, you can install it using the following command:

```bash
sudo apt update
sudo apt install ffuf
```

### Basic Usage

The basic syntax for using ffuf is:

```bash
ffuf -u URL -w WORDLIST
```

- `-u URL`: The target URL you want to scan.
- `-w WORDLIST`: The wordlist file containing the words to be fuzzed.

### Examples

#### Example 1: Basic Scan of a Website

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

In this example, `FUZZ` is a placeholder that ffuf will replace with each word from the specified wordlist.

**Expected Output:**

```
        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1
________________________________________________

 :: Method           : GET
 :: URL              : http://example.com/FUZZ
 :: Wordlist         : /usr/share/wordlists/dirb/common.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

admin                  [Status: 301, Size: 0, Words: 1, Lines: 1]
css                    [Status: 301, Size: 0, Words: 1, Lines: 1]
images                 [Status: 301, Size: 0, Words: 1, Lines: 1]
index.php              [Status: 200, Size: 1111, Words: 100, Lines: 35]
robots.txt             [Status: 200, Size: 17, Words: 2, Lines: 2]
```

The output shows the discovered directories and files, along with their HTTP status codes and other metadata.

#### Example 2: Scan with a Custom Wordlist

```bash
ffuf -u http://example.com/FUZZ -w /path/to/custom_wordlist.txt
```

In this example, we're using a custom wordlist instead of the default one.

**Expected Output:**
The output will depend on the contents of the custom wordlist, but it will be similar to the previous example.

#### Example 3: Recursive Scan

To perform a recursive scan, you can use the `-recursion` and `-recursion-depth` options:

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -recursion -recursion-depth 2
```

This will scan the target website and continue to scan any directories that are discovered, up to a depth of 2 levels.

**Expected Output:**
The output will show the discovered directories and files at each level of the recursive scan.

### Additional Options

ffuf provides a wide range of options to customize your scans, such as:

- `-e`: Specify file extensions to search for (e.g., `.php`, `.html`)
- `-t`: Set the number of concurrent threads
- `-o`: Save the output to a file
- `-H`: Add custom headers to the requests
- `-p`: Add a pause between requests (in milliseconds)

You can explore these options in the ffuf documentation to fine-tune your scans.

Remember to always use ffuf (and any web scanning tool) responsibly and with permission, as unauthorized scanning can be considered illegal in some jurisdictions.



                        ALTERNATIVE
FFUF is a web fuzzer and crawler tool included in Kali Linux. It's used to identify vulnerabilities and weaknesses in web applications by sending multiple requests to the target URL.

**Basic Usage:**

1. Open a terminal in Kali Linux and navigate to the directory where you want to save the results.
2. Use the following command to start FFUF:
```
ffuf -w <wordlist> -u <target_url>
```
- `<wordlist>`: The path to the wordlist file you want to use for fuzzing.
- `<target_url>`: The URL of the web application you want to fuzz.

**Examples:**

#### Example 1: Basic Fuzzing

Fuzzing a website using a default wordlist:
```
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://example.com/FUZZ
```
**Expected Output:**

The output will display a list of found URLs, including their HTTP response codes and response sizes. For example:
```
http://example.com/admin [Status: 200, Size: 1234]
http://example.com/uploads [Status: 200, Size: 567]
http://example.com/config.php [Status: 403, Size: 0]
```
#### Example 2: Fuzzing with a Custom Wordlist

Fuzzing a website using a custom wordlist:
```
ffuf -w /path/to/custom_wordlist.txt -u http://example.com/FUZZ
```
**Expected Output:**

The results will depend on the contents of the custom wordlist. You might see:
```
http://example.com/images [Status: 200, Size: 789]
http://example.com/backup [Status: 200, Size: 123]
```
#### Example 3: Recursive Fuzzing

Fuzzing a website recursively to find directories within found directories:
```
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://example.com/FUZZ -recursion
```
**Expected Output:**

The output will show additional layers of directories if they are found:
```
http://example.com/admin/settings [Status: 200, Size: 456]
http://example.com/admin/settings/config [Status: 403, Size: 0]
```
#### Example 4: Saving Output to a File

Saving the fuzzing results to a file for later analysis:
```
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://example.com/FUZZ -o output.txt
```
**Expected Output:**

The fuzzing results will be saved in `output.txt`, which you can review later.

**Tips:**

* Always ensure you have permission to fuzz the target website.
* Be cautious when using FFUF, as it can generate a significant amount of traffic and potentially lead to detection.
* Analyze the output carefully to identify potential vulnerabilities or sensitive information.


                                 ALTERNATIVE
Here's how to use `ffuf`, a Kali Linux tool, along with examples and expected outputs:

`ffuf` (Fuzz Faster U Fool) is a web fuzzer written in Go. It's used for discovering hidden directories, files, virtual hosts, and more through brute-forcing. It's known for its speed and flexibility.

### Installation

`ffuf` is usually pre-installed in Kali Linux. If not, install it using:

```bash
sudo apt update
sudo apt install ffuf
```

### Basic Usage

The basic syntax for using `ffuf` is:

```bash
ffuf -w <wordlist> -u <url> [options]
```

*   `-w <wordlist>`: The wordlist file containing the potential directory or file names.
*   `-u <url>`: The target URL, using `FUZZ` as a placeholder for the part you want to fuzz.
*   `[options]`: Various options to customize the scan.

### Options

*   `-c`:  Colored output.
*   `-p <proxy_url>`:  Proxy URL.
*   `-t <threads>`: Number of concurrent threads (default: 40).
*   `-recursion`:  Recursive mode.
*   `-r`: Follow redirects.
*   `-v`:  Verbose output.
*   `-o <file>`:  Output file.
*   `-of <format>`: Output format (json, csv, md, ecsv, html).
*   `-fc <response_code>`: Filter HTTP status codes (e.g., `-fc 404,500`).
*   `-fw <word>`: Filter word from response.
*   `-fs <size>`: Filter response size.
*   `-maxtime <seconds>`: Maximum runtime in seconds.
*   `-H "Header: value"`: Add custom header to request.
*   `-b "Cookie: value"`: Add custom cookie to request.

### Examples and Output

1.  **Basic Directory Discovery**

    ```bash
    ffuf -w /usr/share/wordlists/dirb/common.txt -u http://example.com/FUZZ
    ```

    **Example Output:**

    ```
    :: Method           : GET
    :: URL              : http://example.com/FUZZ
    :: Wordlist         : /usr/share/wordlists/dirb/common.txt
    :: Threads          : 40
    :: Matcher          : Response status: 200-299,301-308
    
    
    http://example.com/index.php: [Status: 200, Size: 1234, Words: 200, Lines: 50]
    http://example.com/robots.txt: [Status: 200, Size: 456, Words: 80, Lines: 10]
    http://example.com/css/: [Status: 301, Size: 317, Words: 20, Lines: 5]
    http://example.com/images/: [Status: 301, Size: 317, Words: 20, Lines: 5]
    
    
    [Status: 200, Size: 1234, Words: 200, Lines: 50]
    ```

    This output shows that `ffuf` found `index.php`, `robots.txt`, `images/`, and `css/` on the target server. It also shows the size, words and lines of the responses.
2.  **Fuzzing for Subdomains**

    ```bash
    ffuf -w /usr/share/wordlists/subdomains-top1million-5000.txt -u http://FUZZ.example.com
    ```

    **Example Output:**

    ```
    :: Method           : GET
    :: URL              : http://FUZZ.example.com
    :: Wordlist         : /usr/share/wordlists/subdomains-top1million-5000.txt
    :: Threads          : 40
    :: Matcher          : Response status: 200-299,301-308
    
    
    http://www.example.com: [Status: 200, Size: 3456, Words: 500, Lines: 100]
    http://blog.example.com: [Status: 200, Size: 2345, Words: 350, Lines: 75]
    ```

    This output shows that `ffuf` found the subdomains `www.example.com` and `blog.example.com`.
3.  **Fuzzing POST Requests**

    ```bash
    ffuf -w /usr/share/wordlists/parameter-names.txt -u http://example.com/login.php -X POST -d "username=admin&FUZZ=value"
    ```

    **Example Output:**

    ```
    :: Method           : POST
    :: URL              : http://example.com/login.php
    :: Wordlist         : /usr/share/wordlists/parameter-names.txt
    :: Threads          : 40
    :: Matcher          : Response status: 200-299,301-308
    :: Data             : username=admin&FUZZ=value
    
    
    http://example.com/login.php: [Status: 200, Size: 1234, Words: 200, Lines: 50]
    ```

    This output shows the results of fuzzing POST parameters on the login page.
4.  **Filtering by Status Code**

    ```bash
    ffuf -w /usr/share/wordlists/dirb/common.txt -u http://example.com/FUZZ -fc 403,404
    ```

    This command will exclude responses with HTTP status codes 403 and 404 from the output.
5.  **Saving Output to a File**

    ```bash
    ffuf -w /usr/share/wordlists/dirb/common.txt -u http://example.com/FUZZ -o output.txt
    ```

    This command saves the scan results to `output.txt`.
6.  **Using Multiple Wordlists**

    ```bash
    ffuf -w /usr/share/wordlists/dirb/common.txt,extensions.txt -u http://example.com/FUZZ
    ```

    This command uses both `common.txt` and `extensions.txt` as wordlists.  You need to create a file named `extensions.txt` with file extensions you want to search for. For example, it may contain `.php`, `.txt`, `.html`.

### Notes

*   Ensure you have permission to scan the target.
*   Adjust the number of threads based on your network and the target server's capacity.
*   The effectiveness of `ffuf` depends on the quality of the wordlist.
*   Analyze the output carefully to identify potential vulnerabilities or sensitive information.



                               ALTERNATIVE
FFUF (Fuzz Faster U Fool) is a fast web fuzzer written in Go, primarily used for discovering hidden directories, files, and parameters in web applications. It is particularly useful for penetration testers and security researchers. Here’s how to use FFUF, along with examples and expected outputs.

### Installation

FFUF is included in the Kali Linux distribution. If you need to install it on another system, you can do so using the following command:

```bash
sudo apt install ffuf
```

### Basic Usage

FFUF operates by replacing a placeholder (usually `FUZZ`) in a URL with entries from a wordlist. The basic syntax is:

```bash
ffuf -u <target_url> -w <wordlist>
```

- `-u <target_url>`: The target URL where you want to perform the fuzzing.
- `-w <wordlist>`: The path to the wordlist file.

### Examples

#### Example 1: Fuzzing Directory Paths

To discover hidden directories on a website:

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

**Expected Output:**

```
[Status: 200] [Size: 1234] /admin/
[Status: 403] [Size: 456] /private/
```

This output indicates that the `/admin/` directory is accessible (HTTP 200), while the `/private/` directory returns a forbidden status (HTTP 403) [[1]](https://www.kali.org/tools/ffuf/).

#### Example 2: Fuzzing with Extensions

To search for specific file types, you can use the `-e` option:

```bash
ffuf -u http://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -e .php,.html,.txt
```

**Expected Output:**

```
[Status: 200] [Size: 567] /index.php
[Status: 404] [Size: 0] /notfound.html
```

This shows that the `index.php` file exists, while `notfound.html` does not [[1]](https://www.kali.org/tools/ffuf/).

#### Example 3: Fuzzing POST Requests

FFUF can also be used to fuzz POST parameters. For example, to test a login form:

```bash
ffuf -u http://example.com/login -X POST -d "username=admin&password=FUZZ" -w /usr/share/wordlists/passwords.txt
```

**Expected Output:**

```
[Status: 200] [Size: 1234] Found password: password123
```

This indicates that the password `password123` was successful for the username `admin` [[2]](https://www.freecodecamp.org/news/web-security-fuzz-web-applications-using-ffuf/).

### Conclusion

FFUF is a versatile and powerful tool for web application testing, allowing users to discover hidden resources and test for vulnerabilities efficiently. Its speed and flexibility make it a preferred choice among security professionals.

---
Learn more:
1. [ffuf | Kali Linux Tools](https://www.kali.org/tools/ffuf/)
2. [How to Fuzz Web Applications using FFuf - Web Security Tutorial](https://www.freecodecamp.org/news/web-security-fuzz-web-applications-using-ffuf/)
3. [Fuzz Faster with FFUF. A fast web fuzzer written in Go. | by Axios - Technical Club Of IIIT Lucknow | QuikNapp | Medium](https://medium.com/quiknapp/fuzz-faster-with-ffuf-c18c031fc480)
