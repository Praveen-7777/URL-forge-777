#!/bin/bash

# color codes
red='\033[0;31m'
green='\033[0;32m'
blue='\033[0;34m'
nc='\033[0m' #no color
bold='\033[1m'

#check if httpx is installed
step1() {
        if ! command -v httpx &> /dev/null; then

                echo -e "${red} ${bold}ERROR: ${nc} httpx is not installed. Please install httpx"
                echo -e "${blue}You can install httpx using the following command:${nc}"
                echo -e "${blue}go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest${nc}"
                exit 1
        fi
}


step2(){
if [ "$#" -ne 2 ]; then
        echo "Usage: $0 <URL> <file_path>"
        exit 1
fi
}

step3(){
url=$1
file=$2

if [[ ! "$url" =~ ^https?:// ]]; then
        echo -e "${red} ${bold} ERROR:${nc} Enter a valid URL"
        exit 1
fi

if [ ! -f "$file" ]; then
        echo -e "${red} ${bold} ERROR: ${nc} File not Found: $file"
        exit 1
fi

out="url_out.txt" > "$out"
}

step4(){
while IFS= read -r line; do
        line=$(echo "$line" | xargs)

        [ -z "$line" ] && continue
        concat_url="$url/$line"
        echo "$concat_url">>"$out"
done < "$file"
httpx -sc -title -silent -o "$out" < "$out"

url_count=$(wc -l < "$out")
echo -e "${green}${bold}  Success!${nc} URLs saved to $out ${bold} ${red} ${url_count}  URLs Forged!${nc})."
echo -e "${green} ${bold} Enjoy :) ${nc}"
}

step1
step2 "$@"
step3 "$@"
step4
