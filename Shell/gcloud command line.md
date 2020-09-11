# Create a virtual machine using the gcloud command line

1. In GCP console, on the top right toolbar, click the Open Cloud Shell button.

2. Click Continue.

3. To display a list of all the zones in the region to which Qwiklabs assigned you, enter this partial command gcloud compute zones list | grep followed by the region that Qwiklabs or your instructor assigned you to.
 Your completed command will look like this:

    ```
    gcloud compute zones list | grep us-central1
    ```
4. Choose a zone from that list other than the zone to which    Qwiklabs assigned you

    ```
    gcloud config set compute/zone us-central1-b
    ```
5. To create a VM instance called my-vm-2 in that zone, execute this command:
    ```
    gcloud compute instances create "my-vm-2" \
    --machine-type "n1-standard-1" \
    --image-project "debian-cloud" \
    --image "debian-9-stretch-v20190213" \
    --subnet "default"
    ```
6. Close the cloud shell by typing the command

    ```
    exit
    ```

# Connect between VM instances

By clicking on SSH on `my-vm-2` to open then command prompt, check if my-vm-2 can reach my-vm-1 over the network by:

    
    ping my-vm-1

Notice that the output of the ping command reveals that the complete hostname of my-vm-1 is my-vm-1.c.PROJECT_ID.internal

Press Ctrl+C to abort the ping command and use the ssh command to open a command prompt on `my-vm-1`:

    
    ssh my-vm-1

enter yes to confirm that you do

on my-vm-1, install the Nginx web server:

    sudo apt-get install nginx-light -y

Use the nano text editor to add a custom message to the home page of the web server:

    sudo nano /var/www/html/index.nginx-debian.html

replace YOUR_NAME with your name:
    
    Hi from Nehemiah

Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.

At the command prompt on my-vm-1, execute this command to confirm that the web server is serving your new page

    curl http://localhost/

exit on my-vm-1 and return to my-vm-2

    exit
then 

    curl http://my-vm-1/

Copy the External IP address for my-vm-1 and paste it into the address bar of a new browser tab. You will see your web server's home page, including your custom text.

    