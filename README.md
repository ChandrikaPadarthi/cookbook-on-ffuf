# CookBook-on-Ffuf
Ffuf tool A high-speed web fuzzer developed in Go.FFUF is one of the newest and fastest open-source fuzzing tools available. But before we dive in, let's understand what fuzzing is.

Fuzzing is the process of automatically providing random input to an application to find errors or unexpected behavior. It can also involve discovering hidden directories and files on a web server.

How to install fuff in kali linux:

Commmand: sudo apt-get install fuff

![1](https://github.com/ChandrikaPadarthi/cookbook-on-fuff/assets/107339345/6c65a3ba-b012-4205-b677-239018c5d3ed)

Usage with the command ffuf -h. We can find the help page we can explore the tool with this command

![2](https://github.com/ChandrikaPadarthi/cookbook-on-fuff/assets/107339345/2b3624e4-757c-4470-b9a9-85f3c03a7cd2)

ffuf offers many options for fuzzing.

To specify the position to be fuzzed, use the word "FUZZ" in the ffuf command.

Directory and File Discovery
You can find directories on a website with the following command. It uses the -w flag to provide a wordlist and the -u flag to specify the URL with "FUZZ" as the placeholder for fuzzing.

ffuf -w wordlist.txt -u http://website.com/FUZZ

For file discovery, you can use the same command. To include specific file extensions from the wordlist, use the -e flag.

ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html,.php,.txt

![image](https://github.com/ChandrikaPadarthi/cookbook-on-fuff/assets/107339345/43ffbdef-15a4-4af6-97ef-619dd32b89b0)
ffuf offers options to filter responses by specific status codes, line counts, response sizes, word counts, and regex patterns.


Filtering Options
-mc: Status code
-ml: Number of lines in the response
-mr: Regex pattern
-ms: Response size
-mw: Number of words in the response
Examples

To get responses with status codes 200 and 302, use:
Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html -mc 200,302
Recursion

URL parameters ending with FUZZ support recursion. The -recursion flag activates this, allowing ffuf to fuzz URLs and then fuzz further within the directories it discovers.
-recursion-depth: Specifies the depth of recursion
-maxtime: Sets a maximum time in seconds for the fuzzing process
-maxtime-job: Used with -recursion to set a maximum time for each new job created per directory found

Example:

Command: ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ

In this example, We are fuzzing the directories of geeksforgeeks.org target domain.

![image](https://github.com/ChandrikaPadarthi/cookbook-on-fuff/assets/107339345/397a8759-1f45-4af0-a89a-ef0c45451830)

Example for a maximum fuzzing time of 60 seconds:

Command : ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ -maxtime 60

![image](https://github.com/ChandrikaPadarthi/cookbook-on-ffuf/assets/107339345/ab850c5e-c2d9-43ef-a1a4-a810d339701d)




