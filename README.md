<h1>SAST using Brakeman</h1>


<h2>Description</h2>
This lab focuses on utilizing Brakeman, a powerful Static Application Security Testing (SAST) tool for Ruby on Rails applications. Brakeman performs code analysis and identifies potential security vulnerabilities in Ruby on Rails projects, helping developers uncover and address security weaknesses early in the development process.

During this hands-on lab, participants will gain practical experience in using Brakeman to enhance the security of their Ruby on Rails applications. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>Brakeman</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Linux</b> 

<h2>Program walk-through:</h2>

First, we need to download the source code of the project from our git repository.
Let’s cd into the application so we can scan the app: <br/>

git clone https://gitlab.practical-devsecops.training/pdso/rails.git webapp
cd webapp

<br/>
 
<p align="center">
<img src="https://i.imgur.com/sQoJrz3.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Basically, our system doesn’t have Ruby installed, let’s update apt first: <br/>

apt update

<br/>
 
<p align="center">
<img src="https://i.imgur.com/fKGOP6U.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Then, let’s install Ruby with the following command: <br/>

apt install ruby-full -y

<br/>
 
<p align="center">
<img src="https://i.imgur.com/S8QyhRn.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s install the Brakeman tool to perform static analysis: <br/>

gem install brakeman -v 5.2.1

<br/>
 
<p align="center">
<img src="https://i.imgur.com/b8rKrP2.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We have successfully installed Brakeman, let’s explore the functionality it provides us: <br/>

brakeman -h

<br/>
 
<p align="center">
<img src="https://i.imgur.com/DXJzeCF.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We are using the tee command here to show the output and store it in a file simultaneously: <br/>

brakeman -f json | tee result.json

<br/>
 
<p align="center">
<img src="https://i.imgur.com/A7TLVTd.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Please create this brakeman.ignore file: <br/>
```
cat > brakeman.ignore <<EOF
{
    "ignored_warnings": [
        {
          "fingerprint": "febb21e45b226bb6bcdc23031091394a3ed80c76357f66b1f348844a7626f4df",
          "note": "ignore XSS"
        }
    ]
}
EOF
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/lqzx6cN.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s re-run the scanner: <br/>

brakeman -f json -i brakeman.ignore | tee result.json

<br/>
 
<p align="center">
<img src="https://i.imgur.com/UGFqR7e.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />







<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
