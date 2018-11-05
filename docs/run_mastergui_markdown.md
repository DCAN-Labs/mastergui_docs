1.  On Rushmore, go into **/mnt/max/shared/code/internal/GUIs/mastergui**

    *  If human analysis, run the shell script **go.sh**

    *  If monkey analysis, run the shell script **go\_monkey.sh**

2.  On the Launch Screen, there are three different ways to start a new Mplus Analysis:

    *  Under Create Analysis, click **New MPlus**

    *  File &gt; **New (Ctrl + N)**

    *  Under File, click **MPlus**

3.  Select an MPlus Template

    *  If you are running a regression with or without covariates, select **Blank Model**

        *  *The rest of these instructions will be using the Blank Model template*      

    *  Templates are json files in **/mnt/max/shared/code/internal/GUIs/mastergui/templates/mplus**

        *  If you know how to write mplus syntax, create your own template here

4.  In the **Input Data Review** tab, select your **Non-imaging Data File** CSV

    *  Click **Browse** and select your CSV

    *  You can inspect your data on this tab, but no further action is required

5.  Build your model, by going to the next tab **Model Builder**

    *  Define the paths to your dscalars as voxel data

        *  Click “+” under **Voxelized Columns**

        *  Select the variable in your CSV that has the paths to each subject’s dscalar

        *  **Name for the Voxel Variable**

            *  *\*\*IMPORTANT NOTE\*\** Make sure this variable name is different than the dscalar path variable name, this new variable is what you will put in the model NOT the dscalar path

    *  Define your predicator, covariates and outcome variables under **Additional Model Rules**

        *  Click “+”

        *  For a regression:

            *  On the left side box, select the **outcome** (most likely your **voxel variable** created in the Voxelized Column)

            *  In the middle select “**on**”

            *  On the right, check the boxes for your **covariates** and your **predicator**

                *  Covariates and predicators are treated the same in mplus syntax

    *  Your model in mplus syntax will show up in the Model Box on the right

        *  *\*\*IMPORTANT NOTE\*\** Do not worry about **DATA: FILE is missing.csv;**

            *  This is an incorrect output, your csv is not missing

        *  Check that **Names are** and **USEVARIABLES=** contain all of the variables you want to run in your model

        *  Check that **MODEL:** is correct (it should look the same as your additional model rules)

    *  \*\*IMPORTANT NOTE\*\* You do NOT need to click the box next to your additional model rule OR click Apply – it is unnecessary and has no function

6.  Run the analysis, by going to the next tab **Execute**

    *  Click **Test Analysis**

        *  This runs your model but only with 10 subjects and 10 voxels

              *  This is to test if there anything wrong with your CSV variables

        *  If 10 out of 10 failed go to the Troubleshooting documentation under “Test Analysis Failed”

        *  If 0 out of 10 failed, you can select your **Output Parameters**

7.  Select the output ciftis and output directory for your analysis

    *  Under **Output Parameters,** click “+”

    *  For post-mplus multiple comparisons, the required ciftis are:

        *  STANDARDIZED\_MODEL\_RESULTS-**OUTCOME**\_ON-**PREDICATOR**-**Est\_S\_E**

        *  STANDARDIZED\_MODEL\_RESULTS-**OUTCOME**\_ON-**PREDICATOR**-**P-Value**

    *  Select any other ciftis that you are interested in observing and click “OK”

    *  Select the output directory by going to the **Output** tab

    *  Click **Run Analysis**

    *  Leave the GUI open while the analysis is running, it should take ~20 minutes

8.  Mplus Analysis is complete when the output in the Execute/Status tab says:

9.  Go to the top of the Status screen where it says: **Beginning analysis job, output will be generated in /mnt/max/home/USERNAME/masterguioutput/batches/2018-10-31.15.29.20.221462**

    *  This is the time stamp directory where your cifti results are

10. Go to the **Output** tab to view your cifti results

    *  In the **Batches:** dropdown menu, select the time stamp directory for the analysis you just ran

    *  Under **File Pattern:** select **Ciftis**

        *  Highlight on either the Est\_S\_E, P-Value, or NegLog-P-Value (which is automatically created if you select a P-Value output parameter) and click **Open Cifti** on the same row as **File Pattern:** and to the right of **Refresh**

    *  Your cifti will open in Workbench using a standard human or monkey surface template depending on which version of the mastergui you are running

    *  Once one of your ciftis are open in Workbench, open the others through Workbench via File &gt; Open File

        *  If you try opening each via the mastergui Open Cifti, they will each open in separate Workbench windows
