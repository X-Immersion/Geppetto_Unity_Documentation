# Geppetto_Unity_Documentation
This is the public documentation repository for Geppetto Unity. To download and install the plugin, please log in at: https://create.xandimmersion.com/login?geppetto=true

# GEPPETTO for Unity

Automatic lipsync and facial animation tool for Unity (2021+).

> ⚠️ This tool requires an internet connection to generate animations via the internal API. Once generated, animations can be used offline.  

> ⚠️ The demo scene uses HDRP. To upgrade your project, [click here](https://docs.unity.cn/Packages/com.unity.render-pipelines.high-definition@14.0/manual/Upgrading-To-HDRP)  

> ⚠️ If you get the `Missing compiler required member Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create` error, adjust `API Compatibility Level` in Project Settings.

![Blendshapes in Inspector](/docs/images/geppetto_page1_img1.png)


## Table of Contents

[1. About Blendshapes and Phonemes](#1-about-blendshapes-and-phonemes)  
[2. How to Use the Plugin](#2-how-to-use-the-plugin)  
&nbsp;&nbsp;&nbsp;[2.1.Open the Demo Scene](#21-open-the-demo-scene)  
&nbsp;&nbsp;&nbsp;[2.2. Open the Main Geppetto Windows](#22-open-the-main-geppetto-windows)  
&nbsp;&nbsp;&nbsp;[2.3. Generate with an Existing Audio File (i.e. a Voice Record)](#23-generate-with-an-existing-audio-file-ie-a-voice-record)  
&nbsp;&nbsp;&nbsp;[2.4. Generate with Text Only](#24-generate-with-text-only)  
&nbsp;&nbsp;&nbsp;[2.5. Pauses and Emotion Tags](#25-pauses-and-emotion-tags)  
&nbsp;&nbsp;&nbsp;[2.6. Setup the Meshes and Glossaries](#26-setup-the-meshes-and-glossaries)  
&nbsp;&nbsp;&nbsp;[2.7. Blink Settings](#27-blink-settings)  
&nbsp;&nbsp;&nbsp;[2.8. Eye Dart Settings](#28-eye-dart-settings)  
&nbsp;&nbsp;&nbsp;[2.9. Silence Settings](#29-silence-settings)  
&nbsp;&nbsp;&nbsp;[2.10. Advanced Settings](#210-advanced-settings)\
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [2.10.1. Processing Mode: Local](#2101-processing-mode-local)\
&nbsp;&nbsp;&nbsp;[2.11. Save the Generated Animation Clip](#211-save-the-generated-animation-clip)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.11.1. Create a New Animation Clip](#2111-create-a-new-animation-clip)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.11.2. Add to an Existing Animation Clip](#2112-add-to-an-existing-animation-clip)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.11.3. Apply and Generate](#2113-apply-and-generate)\
[3. Synchronize the Animation Clip and the Audio](#3-synchronize-the-animation-clip-and-the-audio)  
[4. How to Use the Plugin in Runtime](#4-how-to-use-the-plugin-in-runtime)  
&nbsp;&nbsp;&nbsp;[4.1. Open the Runtime Scene](#41-open-the-runtime-scene)  
&nbsp;&nbsp;&nbsp;[4.2. Setup Components](#42-setup-components)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4.2.1. Character Components](#421-character-components)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4.2.2. UI Component](#422-ui-component)  
&nbsp;&nbsp;&nbsp;[4.3. Setup Scripts](#43-setup-scripts)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4.3.1. Runtime General Settings](#431-runtime-general-settings)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4.3.2. Runtime Character Settings](#432-runtime-character-settings)  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4.3.3. Submit Event](#433-submit-event)  
[5. Create or Update a Phoneme Glossary Manually](#5-create-or-update-a-phoneme-glossary-manually)


## 1. About Blendshapes and Phonemes

### Definition

**Blendshape** is a deformation of a mesh to achieve a predefined pose. In the context of facial animation, the blendshapes used are specifically designed to reproduce **phonemes**, which are the smallest units of sound in a language.

**Phonemes** are critical in differentiating words from one another. For example, the words "bit" and "bet" differ by just one phoneme, the "i" sound in "bit" and the "e" sound in "bet."

In animation, a **blendshape of a phoneme** is the transition from a closed mouth to a mouth shape that mimics the pronunciation of the desired sound.

### How to Find Your Blendshapes

When you import your 3D model into the scene, you can find the blendshapes under the **SkinnedMeshRenderer** component.

![Sample Scene](/docs/images/geppetto_page4_img1.png)

If you are working directly in 3D modeling software such as **Blender**, **Maya**, or similar, you can check for and edit your blendshapes within those programs as well.

## 2. How to Use the Plugin

### 2.1 Open the Demo Scene
First, import the package into your Unity project. Then, navigate to: `Scenes/SampleScene` and open it.

![Geppetto Window](/docs/images/geppetto_page5_img1.png)

> ⚠️ **Note**  
> If you encounter the following error:
>
> ![Audio File UI](/docs/images/geppetto_page5_img2.png)
> It means you don't have the required version of **Newtonsoft.Json** or it is not correctly set up in your project.
> Please follow this setup guide: [Setup Instructions](link)

### 2.2 Open the Main Geppetto Windows
To open the Geppetto window, go to the Unity menu: `Window > Geppetto`.

![Text Generation UI](/docs/images/geppetto_page6_img1.png)

![Emotion Tag Example](/docs/images/geppetto_page6_img2.png)

### 2.3 Generate with an Existing Audio File (i.e. a Voice Record)
![Glossary Setup](/docs/images/geppetto_page6_img3.png)
1. In the Geppetto Window, switch to the **"Audio to Animation"** tab.
2. At the top of the window, choose the **Language** for the animation.
   - Available options: English, French, Spanish, Italian, Portuguese, and German.
   - This setting is shared between both the **Text to Animation** and **Audio to Animation** tabs.
3. Click the button to select an **audio file** from your system using the file explorer.

### 2.4 Generate with Text Only
1. In the **Geppetto Window**, select the **"Text to Animation"** tab.
2. The first parameter is the **Language**, which determines the language in which the animation will be generated. There are six options: English, French, Spanish, Italian, Portuguese and German.
   This parameter is shared between both **Text to Animation** and **Audio to Animation** tabs.
3. **Speaker:** Select the voice that will be used to generate the audio.

![Blink Settings](/docs/images/geppetto_page7_img2.png)
   
   > To fill this list, you must set up the **Ariel API Key** under **Advanced Settings**. If the field is empty, click **Fetch Speakers** to retrieve available voices.
4. **Text for the Lip-Sync:**
   Enter the sentence to be used for animation. You can include **pause tags** and **emotion tags** to add natural pauses and express emotions dynamically.  
   → For more on this, see [Section 2.5 - Pauses and Emotion Tags](#25-pauses-and-emotion-tags)

5. **Save the Audio File**
   - Check the **"Save the Audio File"** box to store the generated audio in your project.  
     > *Recommended: Always enable this option to retain the output.*
   - In the **New Audio File Name** field, enter your desired filename.
   - In the **Current Saving Path** field, enter or browse to the desired directory using the file explorer.
   ![Save audio file](/docs/images/geppetto_page8_img1.png)

### 2.5 Pauses and Emotion Tags
In addition to words, you can add **pause** and **emotion** tags to your sentence. **Pause tags** are only available if you generate with text only (Text to Animation tab). The duration of the pause can be defined in **seconds (`s`)** or **milliseconds (`ms`)**.

**Syntax:**
`<pause 1s>`
`<pause 1000ms>`

Emotion tags can be added in **both** Text to Animation and Audio to Animation generation.  
They allow you to insert emotion changes at specific points in a sentence.

The **emotion tag** accepts the following parameters:

| **Parameter**    | **Type**    | **Description** | **Required** | **Default**  |
|------------------|-------------|--------------------------------------------------------------------------------------------------|--------------|--------------|
| `emotion`        | string      | Name of the emotion. Must exist in the emotion glossary.                                         | Yes        | —            |
| `intensity`      | int (0–100) | Defines how strong the emotion is.                                                               | Optional   | 50           |
| `transition`     | int (ms)    | Time (in milliseconds) to transition to the emotion.                                             | Optional   | 200          |
| `function_type`  | string      | Type of function used for interpolation | Optional   | cubic

**Base Syntax:** `<emotion emotion_name intensity int_value transition tran_value function_type function_name>`

**Example with all optional parameters**
![Example optional params](/docs/images/geppetto_page9_img1.png)

**Example without optional parameters**
![Example no optional params](/docs/images/geppetto_page9_img2.png)

> ⚠️ **Note**  
> In order for an emotion to be animated, it must exist in the defined emotion glossary.
You can also **Enable Auto Emotion Tag** to automatically insert emotion tags during animation generation.
> ![Save audio file](/docs/images/geppetto_page9_img3.png)

### 2.6 Setup the Meshes and Glossaries
Use the following fields to configure your phoneme and emotion data, as well as the mesh and blendshapes required for animation generation:

| **Field**                   | **Description** |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Phonemes Glossary** | Choose the phoneme glossary (provided or created in [Section 2.2](#22-open-the-main-geppetto-windows)) that you want to use to create the animation clip. |
| **Emotion Glossary** | Choose the emotion glossary (provided or created in [Section 2.2](#22-open-the-main-geppetto-windows)) for emotion tagging support.|
| **Mesh with Blendshapes**   | Select a GameObject from the Unity scene that has a **SkinnedMeshRenderer** component with the blendshapes list. This will serve as the default mesh and will be automatically used in the **Blink** and **Eye Dart** settings. |

![Setup glossaries](/docs/images/geppetto_page10_img1.png)

If your blendshapes are located across multiple GameObjects, click the **Add Mesh** button to link all necessary GameObjects to the generated animation clip.

![Setup glossaries](/docs/images/geppetto_page10_img2.png)

### 2.7 Blink Settings
To enable automated blinking in the generated animation clip, configure the following fields under the **Blink Settings** section and fill the following information:

| **Field**                        | **Description**                                                                                                                                                                         |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Blink Mesh**                   | Select the GameObject from the Unity scene with a **SkinnedMeshRenderer** that includes the BlendShape(s) used for blinking. This can be the same object used for phoneme animation.   |
| **Add Mesh** _(button)_          | Use this if multiple GameObjects contain blink-related BlendShapes. It allows linking all relevant objects to the animation clip.                                                      |
| **Left Eye Blendshape Name**     | Enter the name of the BlendShape used to blink the **left** eye.                                                                                                                        |
| **Right Eye Blendshape Name**    | Enter the name of the BlendShape used to blink the **right** eye.                                                                                                                       |
| **One BlendShape for Both Eyes** | Check this box if a **single BlendShape** controls blinking for both eyes.                                                                                                              |
| **Blink Interval**               | Define the time interval (in seconds) between two blinks. Default is `2 seconds`.                                                                                                       |
| **Enable Interval Range**        | If enabled, allows specifying a **minimum and maximum** range for the blink interval, instead of a fixed value.                                                                         |
| **Blink Delay**                  | Set the duration (in seconds) for how long the eyes stay closed before reopening. Default is `0.1 seconds` (100 ms).                                                                   |

### 2.8 Eye Dart Settings
To enable automated **eye dart** animation in the generated clip, configure the following settings under the **Eye Dart Settings** section:

| **Field**                                 | **Description**                                                                                                                                                  |
|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Amplitude**                              | Controls the strength of the eye movement. Higher values create more noticeable movement; lower values create subtler motion.                                   |
| **Eyes Mesh**                              | Select the GameObject from the Unity scene with a **SkinnedMeshRenderer** that includes the eye movement BlendShapes.                                            |
| **Same Mesh for Both Eyes**               | Check this if both eyes use the same mesh and should share settings.                                                                                             |
| **Additional Meshes with Eye Blendshapes**| Add more GameObjects containing eye movement BlendShapes. Use **Add Mesh** to link them to the animation clip.                                                  |
| **BlendShapes Names**                     | Section to define the names of the BlendShapes used for each direction of eye movement.                                                                          |
| **Same BlendShape for Both Eyes**         | If the same BlendShape controls movement for both eyes, enable this to apply a single value.                                                                     |
| **Look Left**                              | BlendShape name for the **leftward** eye movement.                                                                                                      |
| **Look Right**                             | BlendShape name for the **rightward** eye movement.                                                                                                     |
| **Look Up**                                | BlendShape name for the **upward** eye movement.                                                                                                        |
| **Look Down**                              | BlendShape name for the **downward** eye movement.                                                                                                      |

### 2.9 Silence Settings
These parameters help distinguish between speech and silence in the audio file. Their optimal values can vary depending on the voice and recording quality.

| **Field**           | **Description**                                                                                             |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| **Silence Threshold** | The maximum intensity (in decibels, dB) considered as **background noise**. Used to detect silent segments. |
| **Silence Duration**  | The **minimum duration** (in seconds) that must pass to be considered a silence. Helps separate speech and pauses. |

### 2.10 Advanced Settings
> ⚠️ **API Keys are included with the base Geppetto plug-in.**  
> If you don’t have any, please contact the X&Immersion team at [contact@xandimmersion.com](mailto:contact@xandimmersion.com).

| **Name** | **Description** |
|---------|-----------------|
| **API Key** | Add your API access for Geppetto (lip sync) and Ariel (voice) to access available speakers in the dropdown. |
| **Audio Start Time (seconds)** | Adds delay between the audio and your animation. Useful when synchronizing phoneme animation with a pre-existing animation clip. For example, set `43` if the phoneme animation should start 43 seconds into an existing 2-minute animation. |
| **Blendshape Animation Range** | Defines the min/max amplitude that a phoneme can reach. Useful for adjusting animation intensity for quiet or loud speech.<br>⚠️ *We strongly recommend setting MinRange to at least 60 or higher.* |
| **Curves Type / Emotion Curves Type** | Controls Unity’s keyframe tangent mode:<br>- Free: Fully manual<br>- Auto: Smoothed by Unity<br>- Linear: Constant rate<br>- Constant: Static value<br>- Clamped Auto: Smoothed but clamped between first/last keyframes |
| **Transition Curve / Emotion Transition Curve** | Defines interpolation behavior between two keyframes. Example: Lerp, SmoothStep, EaseIn, EaseOut, EaseInOut, etc |
| **Transition Rate / Emotion Transition Rate** | Determines the number of added keyframes per transition curve. Higher values create more accurate transitions. |
| **Remove Noise** | Checkbox to filter background noise and improve audio clarity. |
| **Phonemes Format** | Defines phoneme output naming/structure. Choose based on your character system: Classic, ARKit, Maya, MetaHuman, RPM |
| **Quality** | Controls detail and processing level:<br>**Low**: Fastest, CMU phonemizer, no alignment<br>**Normal**: Whisper-based alignment, CMU phonemizer, balanced performance<br>**High**: Torch-based alignment, CMU phonemizer, better realism<br>**Highest**: Torch alignment, IPA phonemizer, highest fidelity |
| **Processing Mode** | Select Local or Remote server processing. You can have more information for the local in section [Section 2.10.1](#2101-processing-mode-local)|

#### 2.10.1 Processing Mode: Local
If the Local option is selected, a **Start Server** button will appear. Click it to launch the server, and wait for the confirmation message in the console indicating that the server is ready. You can also **Stop** or **Start** the server again as needed.

![Processing Local Mode](/docs/images/geppetto_page15_img1.png)

If the server doesn’t start, ensure the following files are present in `Assets/Geppetto/Local`: `_internal`, `models`, and `geppetto.exe`.
If any of these files are missing, please contact [X&Immersion](mailto:contact@xandimmersion.com) to obtain them.

### 2.11 Save the Generated Animation Clip
#### 2.11.1 Create a New Animation Clip
![Create New Animation Clip](/docs/images/geppetto_page16_img1.png)

#### 2.11.2 Add to an Existing Animation Clip
If you want to add lip sync to an existing animation, select the animation here:
![Existing Animation Clip](/docs/images/geppetto_page16_img2.png)

#### 2.11.3 Apply and Generate
Once every parameter is set up, click the **Generate** button in the editor. You can see on the console log if there were errors during the phonemes and emotions generation, i.e: an emotion is not listed in the glossary.

![Apply and Generate 2](/docs/images/geppetto_page16_img4.png)

## 3. Synchronize the Animation Clip and the Audio
When everything is generated, you can create a Timeline `(Window > Sequencing > Timeline)`.

Create an `AnimationTrack`, drag and drop your character in it, drag your AnimationClip.

> ⚠️ **Note**  
> You may need to add the AnimationClip to your character `AnimatorController` beforehand

Create an `AudioTrack`, then drag and drop your object containing the `AudioSource`, followed by the `AudioClip`.

![Timeline](/docs/images/geppetto_page17_img1.png)

You might need to run the project once to ensure the Timeline updates properly.

And that’s it!

## 4. How to Use the Plugin in Runtime
### 4.1 Open the Runtime Scene
First, make sure the package is imported into the project. Then open the `Scenes/RuntimeScene`.

![Open Runtime Scene](/docs/images/geppetto_page18_img1.png)

### 4.2 Setup Components
#### 4.2.1 Character Components
The character GameObject must include **two mandatory components**:

#### Audio Source Component
This is required to play the generated audio clip. You can leave all parameters at their default settings.

![Audio Source Component](/docs/images/geppetto_page19_img1.png)

#### Animation Component
To create and play animations at runtime, a legacy animation setup is required. Follow these steps:

1. Create an **Animation Clip**.
2. Select the clip and open the **Inspector**.
3. Click the **three dots menu** in the top-right corner of the Inspector and choose **Debug** mode.
![Debug mode](/docs/images/geppetto_page19_img2.png)
4. In Debug mode, set the **Animation Type** to `Legacy`.
![Audio Source Component](/docs/images/geppetto_page20_img1.png)
5. Switch back to **Normal** mode.
6. Drag and drop the Animation Clip into the **Animation Component** on your character.
![Animation Component](/docs/images/geppetto_page20_img2.png)

> *This process ensures the animation is compatible with runtime playback using the legacy system.*

#### Optional: Animator Component
For demonstration purposes, we've also included an **Animator** component with an associated **Animator Controller** to play an idle animation when the character is not speaking or animating.

#### 4.2.2 UI Component
An interface has been created to allow users to easily test the plugin. It includes:
- A **text field** to enter custom sentences (you can press `Enter` to submit).
- A second **button** to play the animation.
- A **button** to generate a random sentence.
- A **slider** to rotate the character.

#### ⚠️ UI Not Visible?

If the UI is not showing in the scene, some references may be missing. Follow these steps to fix it:

1. Select the **`UIDocument`** object inside the `GeppettoManager`.
2. In the **Inspector**, ensure that both **`Panel Settings`** and **`Source Asset`** fields are **not empty**.
   - If they are empty, assign the appropriate assets from `Assets/UI Toolkit`.
   ![Panel Settings](/docs/images/geppetto_page21_img1.png)

3. If the UI still doesn’t appear:
   - Click on the **Panel Settings** asset.
   - In the **Inspector**, check that the **`Theme Style Sheet`** field is set.
   - If it’s empty, drag the `UnityDefaultRuntimeTheme` asset from `Assets/UI Toolkit/UnityThemes` into the field.
   ![Theme Stle Sheet](/docs/images/geppetto_page21_img2.png)

This will ensure the interface loads correctly in the scene.

### 4.3 Setup Scripts
To enable runtime functionality, several scripts need to be added to specific GameObjects. Below is an overview of each script and how to use it:

#### 4.3.1 Runtime General Settings
This script contains the general settings for lip-sync generation. You can find it at: `Geppetto/Runtime/RuntimeGeneralSettings`

- Drag this script onto a GameObject in your scene. In this project, it's typically attached to the **`GeppettoManager`**, which manages overall runtime configuration.
- For detailed descriptions of its parameters, refer to [2.10. Advanced Settings](#210-advanced-settings) section.

![Runtime General Settings](/docs/images/geppetto_page22_img1.png)

#### 4.3.2 Runtime Character Settings
This script holds the core configuration for the character used in lip-sync. You can find it at: `Geppetto/Runtime/RuntimeCharacterSettings`.

![Runtime Character Settings](/docs/images/geppetto_page22_img2.png)

The basic parameters shown in this editor are the same as those described in the following sections. Refer to them if you need more detailed explanations:

- **Main Parameters**: See [Generate with text only](#generate-with-text-only)
- **Blink Settings**: See [Blink settings](#blink-settings)
- **Eye Dart Settings**: See [Eye dart settings](#eye-dart-settings)

**Additional Fields:**

- **General Settings**: Reference to the GameObject with the `RuntimeGeneralSettings` script.
- **Animation Clip**: The asset where the generated animation will be saved. See [4.2.1. Character Components](#421-character-components) for more information.
- **Head Bone**: Specifies the character's head bone to enable head movement during speech.

#### 4.3.3 Submit Event
To test Geppetto at runtime, a UI is included for dynamic interaction. You can find the script at: `Geppetto/Runtime/SubmitEvent`.

- Attach this script to the **`UIDocument`** GameObject (commonly found within the `GeppettoManager`).
- Then, drag the character GameObject (the one with `RuntimeCharacterSettings` attached) into the **Character Settings** field in the inspector.

![Runtime Character Settings](/docs/images/geppetto_page23_img1.png)

This setup enables Geppetto to handle real-time text-to-animation generation through the runtime interface.


## 5. Create or Update a Phoneme Glossary Manually
To define how your 3D character responds to phonemes during lip-sync, you’ll need to create or update a **Phoneme Glossary CSV file**.

### Steps

1. Start by duplicating the provided example spreadsheet (e.g., `PhonemeGlossary.csv`) and open it in your preferred application, such as **Microsoft Excel**, **Google Sheets**, or another spreadsheet editor.

2. The spreadsheet contains multiple columns:

   - **Column 1 – `Phoneme`**:  
     A list of 39 phonemes used to animate the character’s speech.

   - **Subsequent Columns – `Blendshape_Name` and `Blendshape_Value` pairs**:  
     - Column 2: First `Blendshape_Name`  
     - Column 3: Corresponding `Blendshape_Value`  
     - Column 4: Second `Blendshape_Name`  
     - Column 5: Corresponding `Blendshape_Value`  
     - ...and so on.

3. For each phoneme (each row in Column 1):

   - In the `Blendshape_Name` columns, enter the blendshapes that visually match the sound of the phoneme.
     > Example: For phoneme **"P"**, you might use blendshapes that tightly close the character's lips.

   - In the corresponding `Blendshape_Value` columns, enter a value between **0 and 100** that defines the intensity of the blendshape.

4. Continue filling in `Blendshape_Name` and `Blendshape_Value` pairs for each phoneme row. Ensure blendshape names are accurate and consistent with your character’s rig.

5. Save the completed spreadsheet as a **CSV (Comma-Separated Values)** file.

6. Open the file in a plain text editor to confirm proper formatting:
   - Each row should contain values separated by commas.
   - Each phoneme should be followed by one or more `Blendshape_Name`, `Blendshape_Value` pairs.

7. If necessary, return to your spreadsheet to make corrections or adjustments. Save and recheck until the format and data are correct.

#### Example : How you would fill it for your Character
![Phoneme CSV Example](/docs/images/geppetto_page25_img1.png)


## Contact
For support, contact **X&Immersion**: [contact@xandimmersion.com](mailto:contact@xandimmersion.com)


[Back to Table of Contents](#table-of-contents)