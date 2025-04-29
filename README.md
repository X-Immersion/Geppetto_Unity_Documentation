# Geppetto_Unity_Documentation
This is the public documentation repository for Geppetto Unity. To download and install the plugin, please log in at: https://create.xandimmersion.com/login?geppetto=true

# GEPPETTO for Unity

Automatic lipsync and facial animation tool for Unity (2021+).

> ⚠️ This tool requires an internet connection to generate animations via the internal API. Once generated, animations can be used offline.  

> ⚠️ The demo scene uses HDRP. [How to upgrade your project](https://docs.unity.cn/Packages/com.unity.render-pipelines.high-definition@14.0/manual/Upgrading-To-HDRP)  

> ⚠️ If you get the `Missing compiler required member Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create` error, adjust `API Compatibility Level` in Project Settings.


---

## Table of Contents

- [1. About Blendshapes and Phonemes](#1-about-blendshapes-and-phonemes)
- [2. How to Use the Plugin](#2-how-to-use-the-plugin)
- [3. Synchronize Audio and Animation](#3-synchronize-audio-and-animation)
- [4. Using the Plugin at Runtime](#4-using-the-plugin-at-runtime)
- [5. Create or Update a Phoneme Glossary](#5-create-or-update-a-phoneme-glossary)

---

## 1. About Blendshapes and Phonemes

Blendshapes are mesh deformations used to animate facial expressions, such as phonemes (speech sounds).
Phonemes like 'p', 'e', or 'k' are mapped to facial blendshapes to simulate speaking.
![Blendshapes in Inspector](/docs/images/geppetto_page1_img1.png)


---

## 2. How to Use the Plugin

### 2.1 Open the Demo Scene
- Import the package
- Open `Scenes/SampleScene`

![Sample Scene](/docs/images/geppetto_page4_img1.png)

### 2.2 Open the Geppetto Window
- Go to `Window > Geppetto`

![Geppetto Window](/docs/images/geppetto_page5_img1.png)

### 2.3 Generate with Audio File
- Choose language
- Upload a `.wav` file
- Click **Generate**

![Audio File UI](/docs/images/geppetto_page5_img2.png)

### 2.4 Generate with Text
- Choose voice (requires Ariel API Key)
- Enter text
- Add emotion and pause tags (optional)

![Text Generation UI](/docs/images/geppetto_page6_img1.png)

### 2.5 Pauses and Emotion Tags
Use tags like `<pause 1s>` or `<emotion happy intensity 70 transition 300>`

![Emotion Tag Example](/docs/images/geppetto_page6_img2.png)

### 2.6 Setup Meshes and Glossaries
Assign glossaries and mesh objects that contain blendshapes.

![Glossary Setup](/docs/images/geppetto_page6_img3.png)

### 2.7 Blink Settings
Configure blink frequency, delay, and blendshape names.

![Blink Settings](/docs/images/geppetto_page7_img2.png)

### 2.8 Eye Dart Settings
Configure eye dart amplitude and direction blendshapes.

![Eye Dart Settings](/docs/images/geppetto_page8_img1.png)

### 2.9 Silence Settings
Adjust silence threshold and duration to refine audio parsing.

![Silence Settings](/docs/images/geppetto_page9_img1.png)

### 2.10 Advanced Settings
Set API keys, animation curves, phoneme formats, and choose between local/remote processing.

![Advanced Settings](/docs/images/geppetto_page10_img1.png)

### 2.11 Save the Generated Animation Clip
- Create a new or use existing clip
- Click **Generate**

![Generate Button](/docs/images/geppetto_page11_img1.png)


---

## 3. Synchronize Audio and Animation
Use Unity Timeline to align animation and audio tracks.

![Timeline Setup](/docs/images/geppetto_page13_img1.png)


---

## 4. Using the Plugin at Runtime

### 4.1 Open the Runtime Scene
Open `Scenes/RuntimeScene`
### 4.2 Setup Components
#### Character:
- Add `AudioSource` and `Animation` components
- Use Legacy mode in the clip

![Runtime Setup](/docs/images/geppetto_page15_img1.png)

#### UI:
Ensure `UIDocument` and theme assets are assigned.

![Runtime UI](/docs/images/geppetto_page16_img1.png)

### 4.3 Setup Scripts
Attach `RuntimeGeneralSettings`, `RuntimeCharacterSettings`, and `SubmitEvent` scripts appropriately.

![Script Setup](/docs/images/geppetto_page17_img1.png)


---

## 5. Create or Update a Phoneme Glossary
Edit `PhonemeGlossary.csv` with appropriate blendshape mappings and save as CSV.

![Phoneme CSV Example](/docs/images/geppetto_page25_img1.png)


---

## Contact
For support, contact **X&Immersion**: [contact@xandimmersion.com](mailto:contact@xandimmersion.com)


