# VSCode Remote SSH

This section is duplicated from the SSH section but is worth repeating here on its own as this is a technique for you to increase your computational power without buying a completely new machine. You can even provision machines with 192gb of ram on AWS - C5 series.

## Using VSCode to Connect to a Remote Server

Visual Studio Code (VSCode) enables you to connect directly to a remote server from within the editor. This allows you to utilize a remote server as your computing environment right from your local machine. You can provision a powerful temporary server to execute your code and shut it down when finished. With this setup, you can transfer your files to the server, run your code, and then retrieve the results back to your local system.

![VSCode Remote SSH](../images/ssh.png)

1. Click the blue connect button in the bottom left
2. Click `Remote-SSH: Connect to Host`
3. Enter `ssh username@server_ip -i ~/.ssh/test_server_key`
4. Click `Connect`
