# Environments
The Ombori Grid Console offers support for multiple environments. This allows you to easily deploy applications to a specific environment, allowing you to test installations through the console without impacting the production environment, or allow you to create a subset of devices that can be updated separately but overall are within the same installaton.

## Creating environments
To create an environment, you need to head over to the environments page in the Ombori Grid console. This is accessible from the "Library" tab in the sidebar and then by clicking on "Environments".

![](/assets/environments-sidebar.png ":size=300 :no-zoom")

From this page you can click on the "Create Environment" button to create a new environment, and then fill in the name and display name and you're done!

## Using Environments
To use an environment, you can configure a device to be set up with your created environment. To do this, you need to head over to the devices page in the Ombori Grid console. This is accessible from the "Library" tab in the sidebar and then by clicking on "Devices".

![](/assets/devices-sidebar.png ":size=300 :no-zoom")

Pick any device you have connected, or [connect a new device](/development/general/adding-device). Then, open the device page, click on the "Screen" tab if this hasn't already been selected, and choose within the dropdown menu under environments the environment you want to use. 

![](/assets/select-device-environment.png ":size=400")


From that moment on, you can deploy applications to the new environment, and only the devices configured to have this environment will be updated.

