# Why-You-Should-SSH-chap01

SSH is a protocol to encrypt connection.
Connection is everywhere in digital life.
We need to operate computer remotely.
We need to call somebody remotely.
If we want to do something remotely such as commucation, then SSH can be used to protect our info security.

SSH tech is not different with password, both are used for protect something we want it to be secret.
But from technical perspective, SSH takes public key encryption, which is more safe and convenient than password verification.

The change from password to SSH will be hard but its convenience deserve to take sometime to config it.

## Get a pair of key
Firstly, you should get a pair of key from the tool called `ssh-keygen`.
Understanding SSH protocol is unnecessary, because you just need to use it, you don't waste time in research.

Understanding such engineering protocol is not a big deal, hence there is no need to get a fully understanding, because we are users, we just want to utilize it in our application ASAP.

Use below code to get a pair of key, including a private key and a public one.
> ssh-keygen -t ed25519 -C "your_email@example.com" -f filename
Public key can be transfer through Internet. 
As convention, private key is so important that you cannot reveal it to anybody, including the person you trust the most.
Because the private key is created belong to only one person.

## Enable ssh-agent
Enabling and starting ssh-agent

Enter code below in Powershell, notice SysAdmin permission.
PS> Get-Service ssh-agent | Set-Service -StartupType Automatic
PS> ssh-agent

Try to add private key
PS> ssh-add .\kusto_key
:: Identity added: .\kusto_key (cherrise28@outlook.com)

After you add a private key, try code to check you are right
PS> ssh-add -l
:: 256 SHA256:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX username@outlook.com (ED25519)

## Git clone from remote to local
Add the SSH public key to your account on GitHub.
This is pretty easy, go to Github settings and check the menu, you will find the way to config your SSH key.
After doing that, you can try below link to check the connection is good or not.
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection

Trying below to clone this repo to your local.
> git clone git@github.com:Kusto-M/SSH-Easy-Play.git

## Git push from local to remote
`Clone` does not need to do verification, because anybody can clone a pulic repo.
What should does need to do verfication is `Git push`.


