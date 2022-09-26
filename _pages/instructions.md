---
title: "How to create the necessary keys to securely create and sign code changes to GitHub.com in Windows"
layout: single
permalink: /instructions/
author_profile: false
classes: wide
---
<style>
.page__content p,
.page__content li,
.page__content dl {
 font-size:20px
}
</style>
This guide will go through the process of creating SSH keys, and GPG keys, telling GitHub which keys are associated with you, and then using them to sign these changes. These keys will allow you to login into GitHub, and verify that the code changes you make are from you, and not someone else.

## Why would you want to do this?

Understandably, a question that you might be asking is. Why would you want to verify with GitHub you are the one creating changes using these types of keys? Since the keys we will generate are used to login, and sign the changes made to the code, and you are the only with the keys after creation since they were created randomly. Using these keys allows GitHub to know it is actually you making these changes, and not someone who hacked their way into your account. Think of it as Two Factor Authentication when you login, but on the work that has happened instead. Using this system is often a common practice for open source projects, as it shows the community using the project no malicious code is being put in by a criminal actor.

## Pre-requisites

- [ ] A Windows Computer
- [ ] A [GitHub](https://github.com) Account
- [ ] When given something to run in the terminal it will look like <b>"Thing to run"</b>, run the bolded part inside of the quotes, this example command would look like the following:
![Command to run](/assets/images/instructions/CommandPromptExample.png)

## Step 0

- If you had a GitHub account prior to starting, and believe that account was created prior to Fall 2018 confirm that you have a verified email address by going to [https://github.com/settings/emails](https://github.com/settings/emails) and checking.

## Step 1 - Install the necessary software on a Windows Computer

<ol type="a">
    <li><h3>Install Git Bash for Windows</h3></li>
    <ol type="i">
        <li>First download the 64-bit version of Git Bash Installer for Windows from <a href="https://git-scm.com/download/win">https://git-scm.com/download/win</a></li>
        <li>Run the installer with at least the options of <b>Windows Explorer integration</b> and <b>Associate .git* configuration files with the default text editor</b> from the first selection menu, then press next.</li>
        <img src="/assets/images/instructions/GitBashInstall1.png" alt="Git Bash Installation with proper slection">
        <li>From this menu select the default text editor. A good idea is changing the default value from VIM to Nano, as it is easier to use.</li>
        <img src="/assets/images/instructions/GitBashInstall2.png" alt="Git Bash Installation with proper slection">
        <li>Then press next leaving all the default values, and then finish the installation with the install button</li>
    </ol>
    <li><h3>Install GNU Privacy Guard</h3></li>
    <ol type="i">
        <li>First download the 64-bit version of Gpg4win installer from <a href="https://gpg4win.org/download.html">https://gpg4win.org/download.html</a>, press the download button, then $0 donation then press download</li>
        <li>Run the installer, select your language then press next.</li>
        <li>When the Choose Components menu comes up, deselect GpgOL box as it will not be used, then press next and finish the installation.</li>
        <img src="/assets/images/instructions/Gpg4WinInstall1.png" alt="Gpg4win install with proper selection">
    </ol>
</ol>

## Step 2 - Creating the SSH Key

<ol type="a">
    <li><h3>Navigating to the SSH Settings Folder</h3></li>
    <ol type="i">
        <li>In the Windows Menu search for <b>Git Bash</b> and open the program. This should come up with a command line.</li>
        <li>Run the following command <b>"cd ~/.ssh"</b>. The ~ character can be created with Shift + key left of 1.</li>
    </ol>
    <ol type="A" start="24">
        <li>If you get an error saying <b>No such file or directory</b> then run the following command <b>"mkdir ~/.ssh"</b> then run the command <b>"cd ~/.ssh"</b> again.</li>
    </ol>
    <li><h3>Making the SSH Key</h3></li>
    <ol type="i">
        <li>Type the following command <b>"ssh-keygen -t ed25519 -C "</b> without pressing enter, this does end in a space.</li>
        <li>Then type your email address from GitHub, and paste it after the <b>"-C "</b> part of the command by right clicking, and type a single quotation mark " then press enter.</li>
        <img src="/assets/images/instructions/SSHKeyGen1.png" alt="Proper ssh-keygen">
        <li>It will now ask for a file name, you can leave it default, but something memorable like <b>GitHubSSHKey</b> is a good idea. Then press enter.</li>
        <li>It will then ask for a few more questions press enter until you see random ascii art similar to the image below. This is the visual representation of the random number use to generate your new key</li>
        <img src="/assets/images/instructions/SSHKeyGen2.png" alt="Random ascii art">
    </ol>
    <li><h3>Confirming the SSH Key was created</h3></li>
    <ol type="i">
        <li>Run the following command <b>"cat GitHubSSHKey"</b> changing the file name if you used something different.</li>
        <li>If what is printed to the command line starts with dashes and <b>BEGIN OPENSSH PRIVATE KEY</b> then more dashes. You have successfully created the key. Leave this window open and move onto the next step.</li>
        <ol type="A" start="24">
            <li>If it does not read like this jump back to step 2b, and run the steps again</li>
        </ol>
        <img src="/assets/images/instructions/SSHKeyGen3.png" alt="SSH Key files">
    </ol>
</ol>

## Step 3 - Creating the GPG Key

<ol type="a">
    <li><h3>Opening the GPG Key Creation Window</h3></li>
    <ol type="i">
        <li>In the Windows Menu again search for and open <b>Git Bash</b></li>
        <li>Run the following command <b>"gpg --full-generate-key"</b></li>
    </ol>
    <li><h3>Creating the key settings</h3></li>
    <ol type="i">
        <li>It will ask for a key type, press enter to select the default value.</li>
        <li>It will then ask for the key size, press type <b>"4096"</b> to set the correct value.</li>
        <img src="/assets/images/instructions/GPGKeyGen1.png" alt="GPG Key Generation">
        <li>It will then ask for the key expiration, press enter to select the default value of no expiry</li>
        <li>Type <b>y</b> and press enter to confirm no expiration</li>
        <img src="/assets/images/instructions/GPGKeyGen2.png" alt="GPG Key Generation">
    </ol>
    <li><h3>Creating the key's user information</h3></li>
    <ol type="i">
        <li>It will then ask for the user's name, type your name and press enter.</li>
        <li>It will then ask for the user's email, type your email that is associated with your GitHub account and press enter.</li>
        <li>It will then ask for a comment, press enter to select the default value of no comment.</li>
        <li>It will then print out the user ID, and ask if it is correct, type <b>O</b> (as in Octopus) and press enter to confirm if it is</li>
        <img src="/assets/images/instructions/GPGKeyGen3.png" alt="GPG Key Generation">
        <li>It will now ask for a passphrase twice by opening up a new windows, you can create a passphrase, or leave it blank</li>
        <ol type="A" start="24">
            <li>If you leave it blank, confirm that no protection is needed</li>
        </ol>
    </ol>
    <li><h3>Confirming the GPG Key was created</h3></li>
    <ol type="i">
        <li>Run the following command <b>"gpg --list-secret-keys --keyid-format=long"</b> there should be a line that begins with <b>sec    rsa4096/</b></li>
            <ol type="A" start="24">
                <li>If this did not happen, rerun the steps starting at step 3b</li>
            </ol>
        <li>If it does, the key was successfully created, and you can move on. Leaving the current command line window open.</li>
        <img src="/assets/images/instructions/GPGKeyGen4.png" alt="GPG Key Confirmation">
    </ol>
</ol>

## Step 4 - Configuring the system to use the newly created keys

<ol type="a">
    <li><h3>Enabling the Windows SSH-Agent key manger to start automatically</h3></li>
    <ol type="i">
        <li>In the Windows Menu search for <b>PowerShell</b>, but do not open it yet</li>
        <li>Right click on the PowerShell icon and select <b>Run as Administrator</b></li>
        <li>In this new powershell windows run <b>"Set-Service ssh-agent -StartupType Automatic"</b> and press enter. This will cause the software managing the keys to run when your computer starts</li>
        <img src="/assets/images/instructions/SSHAgentPowerShell1.png" alt="Running the command in powershell">
        <li>After this succeeds close the powershell window</li>
    </ol>
    <li><h3>Adding the SSH Key to the SSH-Agent</h3></li>
    <ol type="i">
        <li>Go back to the Git Bash window where you made the SSH Key</li>
        <li>Run the following command <b>"eval $(ssh-agent -s)"</b> and press enter. This will start the SSH-Agent</li>
        <li>Then run, <b>"ssh-add ~/.ssh/GitHubSSHKey"</b> replacing the file name with the one you used if you used something different. This will add the key to the SSH-Agent</li>
        <img src="/assets/images/instructions/SSHAgentIdentity1.png" alt="Adding the identity to the agent">
        <li>After this runs, move onto the next step, but do not close the Git Bash window</li>
    </ol>
    <li><h3>Adding the GPG Key to the git key manager</h3></li>
    <ol type="i">
        <li>Go back to the Git Bash window where you made the GPG Key</li>
        <li>The last command ran should be <b>gpg --list-secret-keys --keyid-format=long</b> with an output similar to this. If there isn't, rerun the command.</li>
        <img src="/assets/images/instructions/GPGKeyGen4.png" alt="GPG Key Confirmation">
        <li>Highlight the long string of letters and numbers after <b>sec    rsa4096/</b>, then right click to copy this value. In the example case it is <b>652BE0AB216BAAFC</b>.</li>
        <li>Type, but do not press enter <b>"git config --global user.signingkey "</b>, this does end with a space</li>
        <li>Right click to paste the value you copied in the previous step, and verify it is the same value before pressing enter</li>
        <img src="/assets/images/instructions/GitConfigGPGKey1.png" alt="Adding GPG Key to git">
        <li>Run the following command <b>"git config --global commit.gpgsign true"</b> and press enter. This will enable using that key when make code changes</li>
        <li>After this runs, move onto the next step, but do not close the Git Bash window</li>
    </ol>
</ol>

## Step 5 - Adding the keys to GitHub

<ol type="a">
    <li><h3>Going to the GitHub Keys management Page</h3></li>
    <ol type="i">
        <li>Open a new browser tab and go to <a href="https://github.com/settings/keys">https://github.com/settings/keys</a> and login with your GitHub account</li>
    </ol>
    <li><h3>Adding the SSH Key to GitHub</h3></li>
    <ol type="i">
        <li>Open up the Git Bash window where you made the SSH Key</li>
        <li>Run the command <b>"cat ~/.ssh/GitHubSSHKey.pub"</b> replacing the file name with the one you used if you used something different.</li>
        <li>Highlight the entire output from <b>ss-ed25519</b> to the end of your email address, and right click to copy it</li>
        <img src="/assets/images/instructions/GitHubSSHPublicKey1.png" alt="The public key">
        <li>On the left side of the page, click on <b>New SSH Key</b>, and type in a memorable name for the key in title, and paste the copied text in the key section, then press add.</li>
        <ol type="A" start="24">
            <li>GitHub may now ask you to confirm your password, or do some other form of verification for the account</li>
        </ol>
        <img src="/assets/images/instructions/GitHubSSHPublicKey2.png" alt="The public key in GitHub">
    </ol>
    <li><h3>Adding the GPG Key to GitHub</h3></li>
    <ol type="i">
        <li>Open up the Git Bash window where you made the GPG Key</li>
        <li>Run the command <b>gpg --list-secret-keys --keyid-format=long</b> to list the keys, and right lick to copy the long string of letters and numbers after <b>sec    rsa4096/</b>, in the example case it is <b>652BE0AB216BAAFC</b>.</li>
        <img src="/assets/images/instructions/GPGKeyGen4.png" alt="GPG Key Confirmation">
        <li>Run the command <b>"gpg --armor --export 652BE0AB216BAAFC"</b> replacing the long string of letters and numbers with the one you used if you used something different.</li>
        <li>Highlight the entire output from <b>BEGIN PGP PUBLIC KEY BLOCK</b> to the end with <b>END PGP PUBLIC KEY BLOCK</b> and right click to copy it</li>
        <img src="/assets/images/instructions/GitHubGPGPublicKey1.png" alt="The public key">
        <li>On the left side of the page, click on <b>New GPG Key</b>, create a memorable title, and paste the copied text in the key section, then press add.</li>
        <ol type="A" start="24">
            <li>GitHub may now ask you to confirm your password, or do some other form of verification for the account</li>
        </ol>
        <img src="/assets/images/instructions/GitHubGPGPublicKey2.png" alt="The public key in GitHub">
    </ol>
    <li><h3>Verifying that the keys were correctly added to GitHub</h3></li>
    <ol type="i">
        <li>Go back to the <a href="https://github.com/settings/keys">https://github.com/settings/keys</a> page and verify that both an SSH key and GPG key are now appear.</li>
        <li>If they do you have added the keys to the GitHub successfully. You may now close the Git Bash windows where you made the SSH and GPG Keys</li>
    </ol>
</ol>

## Step 6 - Testing the keys

<ol type="a">
    <li><h3>Creating a new GitHub repository to test in</h3></li>
    <ol type="i">
        <li>Start by going to <a href="https://github.com/new">https://github.com/new</a></li>
        <li>Fill in the repository name, and set wether you want it public or private</li>
        <li>Then click on the <b>Create repository</b> button</li>
        <li>In the quick setup section, make sure that the SSH option is selected.</li>
        <img src="/assets/images/instructions/GitHubNewRepo1.png" alt="Creating a new repository">
        <li>Do not close the page, you will need it in the next step</li>
    </ol>
    <li><h3>Making the test files</h3></li>
    <ol type="i">
        <li>In the Windows Menu search for <b>Git Bash</b> and open it</li>
        <li>Run the command <b>"cd ~/Documents"</b>. This make the work being done in your Documents folder.</li>
        <li>Run the command <b>"mkdir testRepo"</b> to make a new folder called testRepo.</li>
        <li>Run the command <b>"cd testRepo"</b> to go into the your new folder.</li>
        <img src="/assets/images/instructions/LocalGitRepo1.png" alt="Making a folder for it">
        <p>This prompt is slightly different from normal Git Bash, as I am using a different terminal emulator, but the commands are the same.</p>
        <li>Run the command <b>"echo '# Did this work?' >> README.md"</b> to create a new file called README.md, and add the text <b># Did this work?</b> to it.</li>
        <img src="/assets/images/instructions/LocalGitRepo2.png" alt="Creating the files">
    </ol>
    <li><h3>Making the folder a git repository that will go to GitHub</h3></li>
    <ol type="i">
        <li>In the same command window run the command <b>"git init"</b> to make the folder a git repository.</li>
        <li>Run the command <b>"git add README.md"</b> to mark the README to go up to GitHub</li>
        <li>Run the command <b>"git commit -m 'first commit'"</b> to tell the software you want the changes made to actually go to GitHub.</li>
        <img src="/assets/images/instructions/LocalGitRepo3.png" alt="First commit">
    </ol>
    <li><h3>Telling git where to put the files</h3></li>
    <ol type="i">
        <li>Run the command <b>"git branch -M main"</b> to make the main branch the default branch.</li>
        <li>Go back the browser with GitHub open, and copy the SSH link from the quick setup section. It should look similar to <b>git@github.com:testName/testRepo.git</b> where testName is your username and testRepo is what you named the repo.</li>
        <li>Type but do not press enter <b>"git remote add origin "</b>, this ends in space. Then paste the SSH link you copied from GitHub.</li>
        <img src="/assets/images/instructions/LocalGitRepo4.png" alt="Adding the remote">
        <li>Run the command <b>"git push -u origin main"</b> to push the files to GitHub.</li>
        <img src="/assets/images/instructions/LocalGitRepo5.png" alt="Pushing the files">
    </ol>
    <li><h3>See if the commit worked and was verified</h3></li>
    <ol type="i">
        <li>Go back to your web browser with GitHub open and refresh the page</li>
        <li>You should now see the word <b>Did this work?</b> showup on screen</li>
        <img src="/assets/images/instructions/GitHubVerify1.png" alt="First commit">
        <li>Click on the button labeled <b>1 commit</b> in the top right corner, and you should see the commit you just made</li>
        <li>If everything worked, you should have a little green verified badge</li>
        <img src="/assets/images/instructions/GitHubVerify2.png" alt="commit verified">
    </ol>
</ol>

### If you have made it this far, you have successfully set up GitHub to use SSH and GPG keys to verify your commits. Any commits you make to GitHub will now show as verified letting everyone who sees them know that it has to be you who has made the commit.