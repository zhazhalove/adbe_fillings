# adbe_fillings


### Using python, download SEC fillings

```
pip install -U sec-edgar-downloader

from sec_edgar_downloader import Downloader
dl = Downloader("Personal", "foo.bar@baz.com", ".")

# Get all 10-K filings for CIK 796343
dl.get("10-K", "0000796343", download_details=True)

# Get all 10-Q filings for CIK 796343
dl.get("10-Q", "0000796343", download_details=True)
```

### Using PowerShell, copy all files to a single folder since the file names are the same - each file is appened with a random number

```
(Get-ChildItem . -Filter '*.html' -Recurse).FullName | % { Rename-Item -Path $_ -NewName  $_.Insert( $_.Length - 5, "_$(Get-Random)") }
```

### Using Linux command-line, convert SEC filling html file to pdf file

```
sudo apt-get install wkhtmltopdf
```

```
for file in *.html; do
   wkhtmltopdf "$file" "${file%.html}.pdf"
done
```
