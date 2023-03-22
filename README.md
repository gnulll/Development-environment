# Development environment

## My development environment tools
- [Windows](https://www.microsoft.com/en-us/windows?r=1)
- [Google Chrome](https://www.google.com/chrome/)
- [XAMPP](https://www.apachefriends.org/download.html)
- [Java](https://www.oracle.com/br/java/technologies/downloads/)
- [PHP](https://www.php.net/downloads)
- [Dbeaver](https://dbeaver.io/download/)
- [Draw.io - Desktop version](https://www.diagrams.net/)
- [Git](https://git-scm.com/)
- [MariaDB](https://mariadb.org/download/?t=mariadb&p=mariadb&r=10.11.2&os=windows&cpu=x86_64&pkg=msi&m=fder)
- [Apache Netbeans IDE](https://netbeans.apache.org/download/nb17/)

## Setting up a web server 
- Download and install [XAMPP](https://www.apachefriends.org/download.html)
- Add [Xdebug](https://xdebug.org/) extension to XAMPP:
  - Start Apache on XAMPP and access http://localhost/dashboard/ in your browser.
  - Go to the PHPInfo page and select and copy all page.
  - Go to [Xdebug Installation Wizard](https://xdebug.org/wizard), paste the copied page in textarea and click on **Analyse my phpinfo() output** button to get the correct Xdebug file.
  - Follow the given instructions
- Install an SSL certificate to use **https**:
  - Go to `C:\xampp\apache` directory and create a `domains.ext` file.
  - Copy the following text inside the `domain.ext` file:
	```
	authorityKeyIdentifier=keyid,issuer  
	basicConstraints=CA:FALSE  
	keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment  
	subjectAltName = @alt_names  
	[alt_names]  
	DNS.1 = localhost  
	DNS.2 = www.localhost
	```
  - Go to `C:\xampp\apache` and open the `makecert.bat` file with a text editor.
  - At the end of `...server.key -days 365` line add the following command:
    - `-sha256 -extfile domains.ext`  
  - Execute the `makecert.bat` file, answer just the following questions and skip the rest with the RETURN button:
    - `Enter PEM pass phrase:` (a secure password)
    - `Verifying - Enter PEM pass phrase:` (retype the password)
    - `Country Name (2 letter code) [AU]:` (your country code)
    - `Common Name (e.g. server FQDN or YOUR name) []:` (answer with **localhost**)
    - `Enter pass phrase for privkey.pem:` (your password)
  - Go to `C:\xampp\apache\conf\ssl.crt` and execute the `.crt` file.
    - In the **Certificate Store** section select the **Place all certificates in the following store** and choose **Trusted Root Certification Authorities**
