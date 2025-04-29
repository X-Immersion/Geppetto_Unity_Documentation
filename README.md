# Geppetto_Unity_Documentation
This is the public documentation repository for Geppetto Unity. To download and install the plugin, please log in at: https://create.xandimmersion.com/login?geppetto=true

# GEPPETTO for Unity

Automatic lipsync and facial animation tool for Unity (2021+).

> ⚠️ This tool requires an internet connection to generate animations via the internal API. Once generated, animations can be used offline.  
> ⚠️ The demo scene uses HDRP. [How to upgrade your project](https://docs.unity.cn/Packages/com.unity.render-pipelines.high-definition@14.0/manual/Upgrading-To-HDRP)  
> ⚠️ If you get the `Missing compiler required member Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create` error, go to:  
`Edit > Project Settings > Player > Other settings > API compatibility level` and adjust accordingly.

---

## Table of Contents

1. [About Blendshapes and Phonemes](#1-about-blendshapes-and-phonemes)  
2. [How to Use the Plugin](#2-how-to-use-the-plugin)  
   - [Open the Demo Scene](#21-open-the-demo-scene)  
   - [Open the Geppetto Window](#22-open-the-geppetto-window)  
   - [Generate with Audio File](#23-generate-with-audio-file)  
   - [Generate with Text](#24-generate-with-text)  
   - [Pauses and Emotion Tags](#25-pauses-and-emotion-tags)  
   - [Setup Meshes and Glossaries](#26-setup-meshes-and-glossaries)  
   - [Blink Settings](#27-blink-settings)  
   - [Eye Dart Settings](#28-eye-dart-settings)  
   - [Silence Settings](#29-silence-settings)  
   - [Advanced Settings](#210-advanced-settings)  
   - [Save the Generated Animation Clip](#211-save-the-generated-animation-clip)  
3. [Synchronize Audio and Animation](#3-synchronize-audio-and-animation)  
4. [Using the Plugin at Runtime](#4-using-the-plugin-at-runtime)  
   - [Open the Runtime Scene](#41-open-the-runtime-scene)  
   - [Setup Components](#42-setup-components)  
   - [Setup Scripts](#43-setup-scripts)  
5. [Create or Update a Phoneme Glossary](#5-create-or-update-a-phoneme-glossary)

---

## 1. About Blendshapes and Phonemes

- **Blendshapes** are mesh deformations used to animate facial expressions.
- **Phonemes** are the smallest units of sound (e.g., "p", "e", "k").
- Phoneme blendshapes create facial movements corresponding to speech sounds.

---

## 2. How to Use the Plugin

### 2.1 Open the Demo Scene
- Import the package.
- Open `Scenes/SampleScene`.

### 2.2 Open the Geppetto Window
- Go to `Window > Geppetto`.

### 2.3 Generate with Audio File
- Select "Audio to Animation".
- Choose your language.
- Upload an audio file (WAV recommended).
- Click Generate.

### 2.4 Generate with Text
- Select "Text to Animation".
- Choose language and voice (requires Ariel API key).
- Enter your sentence.
- (Optional) Add emotion or pause tags.
- Click Generate.

### 2.5 Pauses and Emotion Tags

- **Pauses**:  
`<pause 1s>` or `<pause 500ms>`  
- **Emotions**:  
`<emotion happy intensity 70 transition 300 function_type cubic>`

You can also enable automatic emotion tagging.

### 2.6 Setup Meshes and Glossaries

- Assign your phoneme glossary and emotion glossary.
- Link the mesh with blendshapes (usually a `SkinnedMeshRenderer`).

### 2.7 Blink Settings

- Define left/right blink blendshapes.
- Set blink interval and delay.

### 2.8 Eye Dart Settings

- Assign eye movement blendshapes.
- Configure amplitude and directional settings.

### 2.9 Silence Settings

- Adjust silence threshold (in dB) and minimum silence duration (ms).

### 2.10 Advanced Settings

- Add your **Geppetto** and **Ariel** API keys.
- Configure animation range, transition curves, quality (Low → Highest), processing mode (Local or Remote).
- Choose phoneme formats (Classic, ARKit, MetaHuman, etc.).

### 2.11 Save the Generated Animation Clip

- Create a new clip or apply to an existing one.
- Press **Generate** to finalize.

---

## 3. Synchronize Audio and Animation

- Use Unity Timeline (`Window > Sequencing > Timeline`).
- Add both `AnimationTrack` and `AudioTrack`.
- Assign your clips.
- Hit Play to test.

---

## 4. Using the Plugin at Runtime

### 4.1 Open the Runtime Scene

- Open `Scenes/RuntimeScene`.

### 4.2 Setup Components

#### Character Components

- Add `AudioSource` and `Animation` components.
- Mark your clip as "Legacy" in debug inspector mode.

#### UI Component

- The UI allows sentence input and playback.
- Make sure `UIDocument` has correct panel and theme assets.

### 4.3 Setup Scripts

#### 4.3.1 Runtime General Settings

- Add the `RuntimeGeneralSettings` script to `GeppettoManager`.

#### 4.3.2 Runtime Character Settings

- Add `RuntimeCharacterSettings` to the character.
- Assign animation clip, general settings, and head bone.

#### 4.3.3 Submit Event

- Attach `SubmitEvent` script to the UI.
- Link the character.

---

## 5. Create or Update a Phoneme Glossary

1. Duplicate and edit `PhonemeGlossary.csv`.
2. Each row:  
   - Column 1: Phoneme name  
   - Column 2+: Blendshape name + value (0–100) pairs
3. Save as `.csv`.
4. Test by opening in a text editor.

---

## Contact

For support, contact **X&Immersion** at:  
📧 [contact@xandimmersion.com](mailto:contact@xandimmersion.com)

---

**Enjoy animating with GEPPETTO!** 🎭


