# Google Cloud Fundamentals: Getting Started with App Engine

## You can list the active account name with this command:
    gcloud auth list

Output:

    Credentialed accounts:
    - <myaccount>@<mydomain>.com (active)
Example output
    
    Credentialed accounts:
    - google1623327_student@qwiklabs.net

You can list the project ID with this command:

    gcloud config list project

Output

    [core]
    project = <project_ID>

Example output:

    [core]
    project = qwiklabs-gcp-44776a13dea667a6

# Initialize App Engine

## Initialize your App Engine app with your project and choose its region
    gcloud app create --project=$DEVSHELL_PROJECT_ID

When prompted, select the region where you want your App Engine application located.

Clone the source code repository for a sample application in the hello_world directory:

    git clone https://github.com/GoogleCloudPlatform/python-docs-samples

Navigate to the source directory:
     
     cd python-docs-samples/appengine/standard_python3/hello_world

# Run Hello World application locally

### Execute the following command to download and update the packages list.

    sudo apt-get update

Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system

    sudo apt-get install virtualenv

If prompted [Y/n], press Y and then Enter.

    virtualenv -p python3 venv

Activate the virtual environment

    source venv/bin/activate

Navigate to your project directory and install dependencies.

    pip install  -r requirements.txt

Run the application:

    python main.py

In Cloud Shell, click Web preview, Preview on port 8080 to preview the application

# Deploy and run Hello World on App Engine

### Navigate to the source directory:

    cd ~/python-docs-samples/appengine/standard_python3/hello_world

Deploy your Hello World application.

    gcloud app deploy

`If prompted "Do you want to continue (Y/n)?", press Y and then Enter.`

Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com

    gcloud app browse

You can disable the application when you;re done previewing because GCP does not offer a way to undeploy an application.


