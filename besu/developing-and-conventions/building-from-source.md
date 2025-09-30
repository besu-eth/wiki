# Building from source

## **Prerequisites** 

- Java 21 (NEW since [https://github.com/hyperledger/besu/pull/7177](https://github.com/hyperledger/besu/pull/7177))
  - note that gradle 8.7 is incompatible with Java 22, you need Java 21
  - eg if installing java via homebrew,
    - brew install openjdk@21
- For Mac installations: MacOS High Sierra 10.13 or later
- For Windows: Besu is currently supported only on 64-bit versions of Windows, and requires a 64-bit version of JDK/JRE. We recommend that you also remove any 32-bit JDK/JRE installations.

## **Checkout source code**

git clone --recursive git@github.com:hyperledger/besu.git

or

git clone --recursive https://github.com/hyperledger/besu  

## **Create a fork**

If you're going to do development, to submit a PR you'll need to push a branch to your fork and create the PR from that (you can't push a branch to the main repo).

git clone --recursive git@github.com:hyperledger/besu.git  
\# this will check out a working copy of the main besu repo, in a directory called besu  
cd besu  
git remote -v  
\# this will show you have origin remote pointing to the main besu repo  
\# also create a fork in the github UI - so that will end up at github.com/your-github-user/besu  
git remote rename origin upstream  
git remote add origin git@github.com:your-github-user/besu.git  
\# git push will push to origin by default, which is now your fork of besu

## **See what tasks are available** 

To see all of the gradle tasks that are available:

cd besu ./gradlew tasks

## **Build from source**

Build the distribution binaries: 

cd besu  
./gradlew installDist

## **Run from the binaries you built from source**

To see help menu:

`cd build/install/besu`  
`./bin/besu --help`

Run Besu with default options (by default this stores all persistent data in `build/install/besu`):

`cd build/install/besu`  
`./bin/besu` 

To set custom CLI options:

cd build/install/besu  
./bin/besu --discovery-enabled=false --data-path=/tmp/besutmp

## **Building and Running on Windows**

Note: On Windows, to run gradlew, you must have the JAVA\_HOME system variable set to the Java installation directory. For example: 

JAVA\_HOME = C:\\Program Files\\Java\\jdk21.0\_181

Note: If you are using WSL (Windows Subsystem for Linux) with Ubuntu to build and run Besu using DNS discovery, you might need to change the default DNS provided by Windows. See issue [https://github.com/hyperledger/besu/issues/3046](https://github.com/hyperledger/besu/issues/3046) for more detail.

## **Running tests**

### **Dependencies**

There are two dependencies required if you want to run the tests: libsodium version 1.0.16 or higher and libnss version 3.35 or higher.

*If you are not planning on running the tests, you can skip this step.*

To install the dependencies type in the following commands on MacOS or Ubuntu.

MacOS:  
$ brew install libsodium nss  
  
Ubuntu (16.04 LTS):  
$ apt install libsodium18 libnss3  
  
Ubuntu (18.04 LTS):  
$ apt install libsodium23 libnss3  
  
Ubuntu (20.04 LTS):  
$ apt install libsodium23 libnss3  
  
Ubuntu (14.04 LTS):

For libsodium you can find the appropriate package (v1.0.16-0) files here:  
[https://launchpad.net/ubuntu/+source/libsodium](https://launchpad.net/ubuntu/+source/libsodium)  
[https://launchpad.net/~phoerious/+archive/ubuntu/keepassxc/+sourcepub/8814980/+listing-archive-extra](https://launchpad.net/~phoerious/+archive/ubuntu/keepassxc/+sourcepub/8814980/+listing-archive-extra)  
  

For libnss you can find the appropriate package (v3.35) files here:  
[https://packages.ubuntu.com/bionic/libnss3](https://packages.ubuntu.com/bionic/libnss3)

  
The \`sudo\` command might be needed on Linux, and if the screen prompts you to enter a password, type your password and press enter.

cd besu  
./gradlew build  
./gradlew integrationTest LTS