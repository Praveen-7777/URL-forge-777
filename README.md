URL Forge is a simple script for URL building during directory and file fuzzing. This tool automates the process of constructing full URLs from a base URL and a list of paths, then uses httpx to retrieve status codes and page titles for further enumeration.

#Usage

Ensure httpx is Installed URL Forge requires httpx for checking the status codes and page titles of the URLs. You can install it using:

go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
Run the script with the base URL and the path to the file containing the list of paths

./url-forge.sh <URL> <file_path>
