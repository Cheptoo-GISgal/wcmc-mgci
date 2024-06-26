Initial set-up
=================

QGIS software installation
^^^^^^^^^^^^^^^^^^^^^^^^^^
Ensure QGIS 3.22.16 installed on your computer. We suggest users use the Long-Term Release version of QGIS to undertake their analysis as this is the most stable version and users are less likely to incur technical difficulties and bugs. There are various installers depending on your operating system but for most users we recommend the QGIS Standalone Installer. Full instructions are on their website: https://qgis.org/en/site/forusers/download.html.

While the QGIS-SDG 15.4.2 beta analysis runs entirely within the QGIS interface, to run this workflow, you will also need to install R Software 4.4.1. R scripts will be run from within the QGIS interface and no prior knowledge of R is required. There have been a number of releases since 4.4.1 we have found that some of the later versions cause the r-scripts to run slower within the toolbox.


R software and packages installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Download and install R from https://www.r-project.org/ and then download and install RStudio Desktop from https://www.rstudio.com/products/rstudio/. 
A step-by-step guide on how to install R and R Studio (with images) can be found in Annex 1.

It is important to use a current version of R software (we currently recommend R-4.1.1). Although there have been a number of releases since 4.4.1,  we have found that some of the later versions cause the r-scripts to run slower within the QGIS toolbox. If you already have R installed, the R version can be easily checked on the text within the ‘R Console’ box at the beginning of a new session (see Figures below for standalone R and  R Studio). You can have multiple versions of R installed on your computer at a time so if you don’t have this version.

|image5|

|image6|

QGIS-SDG 15.4.2 custom toolbox download and installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Users will also need to download the SDG_15_4_2_beta_Toolbox and set of templates and style files from the SDG_15_4_2_beta repository. In a web browser navigate to the SDG15.4.2 beta repository using the following URL: **https://github.com/sepal-contrib/wcmc-mgci/tree/main**

- Click on **Code>>Download ZIP**

  |setup1|

- Next open a file explorer window and navigate to the folder where you have downloaded the file. At this stage we would recommend you move the zip file to a sensible location with a short and simple file structure. e.g. in this example we have moved the downloaded zip file to **c:\\workspace**. Right-click on the file named **wcmc-mgci-main.zip** and click on **7-ZIP >>Extract here**.
   
  |setup2|

- Once unzipped you should see a folder of the same name (**wcmc-mgci-main**). Navigate inside this folder and you should see the following file structure and a zip file called **SDG15_4_2_beta.zip**.
   
  |setup2b|
   
- Right-click on **SDG15_4_2_beta.zi** and click on **7-ZIP>>Extract file**. Note we are clicking on extract files this time and not extract here as we want to make some modifications to the path we are unzipping to.

  |setup3|

- You should see the unzip files window below. Do NOT click OK yet as we want to make some changes.

  |setup4|

- First remove **'wcmc-mgci-docs-main’** from the extract to path and then tick **Eliminate duplication of root folder**.

  |setup5|

  |setup6|

- Click okay once you have done these steps. You should now have a folder set up for the QGIS processing. Please do not alter the folder structure as the tools rely on these to remain intact.

  |setup7|

- The next step is to go into the input_data folder and unzip the Global mountains map. Right-click on **SDG1542_WorldMountainMap.zi** and click on **7-ZIP>>Extract here**.

  |setup8|

You are now ready to open the QGIS project. Double-click to **SDG_15_4_2_beta.qgz** to open the project.

|setup9|

QGIS plugins installation
^^^^^^^^^^^^^^^^^^^^^^^^^

Next (once QGIS is open) there are a few steps that need to be undertaken to set up the QGIS project correctly and to link it to the custom toolbox and scripts.

First you will need to install the following plugins:

**Processing R Provider:** This plugin essentially allows R scripts
to be used directly within the QGIS processing toolbox with the
simple addition of some QGIS header information placed at the top of
the script to making the R script behave exactly like other
processing tools in the QGIS processing toolbox. The header
information allows graphical fields to be set in the processing
dialogue window when running the tool e.g. the input raster, a
specific field or the location and name of an output raster. Some
header information is used to tell QGIS to either pass information to
R and from QGIS about the tool to enable the R processing to happen
within the QGIS interface.

-  From the QGIS Menu Toolbar click on **Plugins>>Manage and Install Plugins**
   
   |image9|

-  From the Plugin dialogue window search for **processing R**
   
   |image10|

-  Click **Install Plugin** and then **Close**

The Processing R Provider has now been installed.

QGIS settings
^^^^^^^^^^^^^

Next some QGIS settings will be changed to ensure QGIS knows where to find the R installation, scripts and model folders. 

- From the main menu select **settings>>processing**. Click on **providers** and expand the **R** tab. Double click on the **R-scripts folder** path to expose the three dots. Click on this and click **Add**. Navigate to the R_scripts folder in the SDG15_4_2_beta folder. e.g. in this example **C:\\workspace\\SDG15_4_2_beta\\R_scripts**. Then click **OK**.
   
  |setup13|
   
- Double-click on the **R folder path** and navigate to where you have installed your R software. This is to tell QGIS where to run R from. i.e. to check the R folder is pointing to the correct location (where it is installed on your computer)
   
  |setup14|   
   
  - If you operating system is 64 bit, tick Use **64bit version**
  - Click **OK**
   
- In the same **settings>>processing** window, shrink down the R tab and expand **Model**. Double click on the models path to expose the three dots. Click on this and click **Add**.

- Navigate to the QGIS models folder in the SDG15_4_2_beta folder. e.g. in this example **C:\\workspace\\SDG15_4_2_beta\\QGIS_models**. Then click **OK**.

  |setup12|
   
- Next on the left hand panel click on **Data Sources** and change the **Representation of null values** from Null to **NA** (this will ensure  the correct NA representation of Null values in the output reporting tables).
   
  |setup10|

- In the same settings window click on **processing>>general** and change the **Results group name** to **OUTPUTS**. Put this in capitals as this is how it will then appear in the QGIS table of contents. It means that any outputs from geoprocessing tools will be stored under this group heading and makes it easier to distinguish from the INPUT data.
   
  |setup11|

- Once done click **OK** to close the setting window and return to the main QGIS interface.
   
- On the righ-hand side of QGIS you should see the processing Toolbox. (If it is not visible, from the main menu select **View>>panels>>processing toolbox**).

- You should also see that the R script button has appeared on the processing toolbox menu and R scripts tab visible in the toolbox.

  |image17|

  |image12|

- In the processing toolbox if you expand models and R you should see the SDG15.4.2 models and scripts present.  It is from the toolbox that you will run the tools if you choose to use the **SDG_15_4_2_beta toolbox** rather than undertaking the manual steps.
   
  |setup15|

-  Save the QGIS project. 


Optional step: Add the **Resource sharing plugin:** This plugin is a useful R related plugin (which is not essential for the MGCI but useful for users  wishing to integrate R with QGIS).

*Once the resource sharing plugin is installed some additional scripts will also be visible. They are grouped into several categories as in the screengrab below.*

|image30|

- To add this plugin click on **plugins>>resource sharing>>resource sharing**
   
  |image18|
   
- Click on **All Collections** on the left hand panel and click **QGIS R script collection (QGIS Official Repository)** then click **Install**
   
  |image19|

- The wider collection of scripts should now be present in the R-scripts collection. These are not required for MGCI but useful for R-Integration with QGIS.
   
  |image20|

For further information see the following sections of the QGIS user  manual at

https://docs.qgis.org/3.28/en/docs/user_manual/processing/3rdParty.html#r-libraries



.. |setup1| image:: media_toolbox/setup1.png
   :width: 800
.. |setup2| image:: media_toolbox/setup2.png
   :width: 800
.. |setup2b| image:: media_toolbox/setup2b.png
   :width: 800
.. |setup3| image:: media_toolbox/setup3.png
   :width: 800
.. |setup4| image:: media_toolbox/setup4.png
   :width: 800
.. |setup5| image:: media_toolbox/setup5.png
   :width: 800
.. |setup6| image:: media_toolbox/setup6.png
   :width: 800
.. |setup7| image:: media_toolbox/setup7.png
   :width: 800
.. |setup8| image:: media_toolbox/setup8.png
   :width: 800
.. |setup9| image:: media_toolbox/setup9.png
   :width: 800
.. |setup10| image:: media_toolbox/setup10.png
   :width: 800
.. |setup11| image:: media_toolbox/setup11.png
   :width: 800
.. |setup12| image:: media_toolbox/setup12.png
   :width: 800
.. |setup13| image:: media_toolbox/setup13.png
   :width: 800
.. |setup14| image:: media_toolbox/setup14.png
   :width: 800
.. |setup15| image:: media_toolbox/setup15.png
   :width: 800

.. |image0| image:: media_QGIS/image2_orig.png
   :width: 6.26806in
   :height: 3.16875in
.. |image1| image:: media_QGIS/image3_orig.png
   :width: 6.26806in
   :height: 5.06528in
.. |image2| image:: media_QGIS/image4_orig.png
   :width: 6.26806in
   :height: 0.81458in
.. |image3| image:: media_QGIS/image5_orig.png
   :width: 6.26806in
   :height: 1.65347in
.. |image4| image:: media_QGIS/image6_orig.png
   :width: 6.26806in
   :height: 3.97847in
.. |image5| image:: media_QGIS/image7_orig.png
   :width: 5.97917in
   :height: 4.25867in
.. |image6| image:: media_QGIS/image8_orig.png
   :width: 6.03472in
   :height: 4.75909in
.. |image7| image:: media_QGIS/image9_orig.png
   :width: 6.26806in
   :height: 4.46458in
.. |image8| image:: media_QGIS/image10_orig.png
   :width: 6.26806in
   :height: 3.33742in
.. |image9| image:: media_QGIS/image11_orig.png
   :width: 5.52160in
   :height: 0.94805in
.. |image10| image:: media_QGIS/image12_orig.png
   :width: 6.26806in
   :height: 3.70278in
.. |image11| image:: media_QGIS/image13_orig.png
   :width: 4.42770in
   :height: 4.71941in
.. |image12| image:: media_QGIS/image14_orig.png
   :width: 4.42653in
   :height: 4.71816in
.. |image13| image:: media_QGIS/image15_orig.png
   :width: 3.44840in
   :height: 1.83359in
.. |image14| image:: media_QGIS/image16_orig.png
   :width: 0.43750in
   :height: 0.35417in
.. |image15| image:: media_QGIS/image17_orig.png
   :width: 3.21875in
   :height: 1.13542in
.. |image16| image:: media_QGIS/image18_orig.png
   :width: 6.26806in
   :height: 2.56667in
.. |image17| image:: media_QGIS/image19_processingtoolboxR2.png
   :width: 2.32263in
   :height: 0.97904in
.. |image18| image:: media_QGIS/image20_orig.png
   :width: 6.26806in
   :height: 3.45417in
.. |image19| image:: media_QGIS/image21_orig.png
   :width: 5.21948in
   :height: 1.75024in
.. |image20| image:: media_QGIS/image22_orig.png
   :width: 1.95347in
   :height: 2.17361in
.. |image21| image:: media_QGIS/image23_orig.png
   :width: 5.10417in
   :height: 1.21875in
.. |image22| image:: media_QGIS/image24_orig.png
   :width: 5.75000in
   :height: 3.93750in
.. |image23| image:: media_QGIS/image25_orig.png
   :width: 0.29861in
   :height: 0.29276in
.. |image24| image:: media_QGIS/image26_orig.png
   :width: 6.26806in
   :height: 3.40417in
.. |image25| image:: media_QGIS/image27_orig.png
   :width: 6.26806in
   :height: 3.59931in
.. |image26| image:: media_QGIS/image28_orig.png
   :width: 3.18056in
   :height: 2.63633in
.. |image27| image:: media_QGIS/image29_orig.png
   :width: 6.26806in
   :height: 2.40000in
.. |image28| image:: media_QGIS/image30_orig.png
   :width: 5.48788in
   :height: 5.13889in
.. |image29| image:: media_QGIS/image31_orig.png
   :width: 5.43750in
   :height: 3.10009in
.. |image30| image:: media_QGIS/image32_orig.png
   :width: 3.37547in
   :height: 4.79234in
