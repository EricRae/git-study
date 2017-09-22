- What's SSH

  Using the SSH protocol, you can connect and authenticate to remote services . With SSH keys , you can connect to GitHub without supplying your username or password at each visit.

- Checking for existing SSH keys

  Before you generate an SSH key , you can check to see if you have any existing keyss.

  ```powershell
  #List the file in your .ssh directory, if they exist
  $ls -al ~/.ssh
  ```

  if exists, you can see the filename of the public keys are one of the following:

  ```powershell
  id_dsa.pub
  id_ecdsa.pub
  id_ed25519.pub
  id_rsa.pub
  ```

- Generating a new SSH

  if you do not already have an SSH key, you must generate a new SSH key .you can generate a new SSH use these followings:

  Paste the text below:

  ```powershell
  $ssh-keygen -t rsa -b 4096 -C "your_email@exmple.com" 
  ```

  this create a new ssh key , using the provided email as a label.

  ```powershell
  Generating public/private rsa key pair.
  ```

  when you are prompted to "Enter a file in which to save the key", please Enter. This accepts the default file location

  ```powershell
  Enter a file in which to save the key (home/you/.ssh):[press Enter]
  ```

  at the prompt, type a secure passphrase .

  ```powershell
  Enter passphrase (empty for no passphrase): [Type a passphrase]
  Enter same passphrase again: [Type passphrase again]
  ```

- Adding your SSH key to the ssh-agent

  Start the ssh-agent in the background

  ```powershell
  $eval "(ssh-agent -s)"
  ```

  Add your SSH private key to the ssh-agent.

  ```powershell
  $ssh-agent ~/.ssh/id_rsa
  ```

- Add the SSH key to your GitHub account

  1. Copy the SSH key to your clipboard

  ```powershell
  #Downloads an installs xclip.if you do not have
  $sudo apt-get install xclip
  #Copies the contents of the id_rsa.pub file to your clipboard
  $xclip -sel clip < ~/.ssh/id_rsa.pub
  ```

  2. In the upper -right corner of github page,click your profile photo, then click *Settings*

     ![Selection_001](/home/eric/Pictures/Selection_001.png)

     1. In the user setting sidebar , click *SSH and GPG keys*.

     2. Click **New SSH key ** or **Add SSH key**.

     3. In the "Title" field, add a descriptive label for the new key

     4. Paste your key into the "Key" field.

     5. Click **Add SSH key**.

     6. if prompted , confirm your GitHub password.

     7. Testing your SSH connection

        ```powershell
        $ssh -T git@github.com
        ```

        that ,if you try to use SSH	 connect to the github ,you may see some warning information and you should choose yes . then you can see these information that the SSH 	is right to connecting.

        ```powershell
        $ ssh -T git@github.com
        Hi EricRae! You've successfully authenticated, but GitHub does not provide shell access.  
        ```

