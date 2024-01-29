# Projet de Fin d'Etudes

## Membres

Dylan DELORME LUNA - PEI

Jules MANIGNE-MALAN - PEI

Marie MELONI - PEI

Alexandre HALBOUT - Energie

Mateo BOURDAIN - Energie

Ali MROUE - SI

## Synthèse

Le projet consiste à développer un outil technique, sous la forme d’une application téléphone android ou ios, qui permettrait avant tout de percevoir des changements d’affichage au niveau des feux piétons dans les agglomérations. Chaque utilisateur, potentiel, dans notre cas les déficients visuels ( DV  - Personnes présentant des troubles aigus en terme de vision, caractérisés par des troubles de couleur ou encore une déficience visuelle motrice quasi totale ), pourraient, à l’aide de notre outil, se ballader librement dans les zones urbaines et recevoir des indications sur l’état de chaque passage piéton observé. 

Les instructions suivantes permettent d'expliquer comment monter cette application depuis son propre PC.

Une partie des instructions proviennent de la documentation officielle de Tensor Flow Lite, le logiciel permettant de détecter les objets.

<!-- TODO(b/124116863): Add app screenshot. -->

### Model

We provide 4 models bundled in this App: MobileNetV1 (float), MobileNetV1
(quantized), EfficientNetLite (float) and EfficientNetLite (quantized).
Particularly, we chose "mobilenet_v1_1.0_224" and "efficientnet-lite0".
MobileNets are classical models, while EfficientNets are the latest work. The
chosen EfficientNet (lite0) has comparable speed with MobileNetV1, and on the
ImageNet dataset, EfficientNet-lite0 out performs MobileNetV1 by ~4% in terms of
top-1 accuracy.

For details of the model used, visit
[Image classification](https://www.tensorflow.org/lite/models/image_classification/overview).

Downloading, extracting, and placing the model in the assets folder is managed
automatically by download.gradle.

## Requirements

*   Android Studio 3.2 (installed on a Linux, Mac or Windows machine)

*   Android device in
    [developer mode](https://developer.android.com/studio/debug/dev-options)
    with USB debugging enabled

*   USB cable (to connect Android device to your computer)

## Build and run

### Step 1. Clone the TensorFlow examples source code

Clone the TensorFlow examples GitHub repository to your computer to get the demo
application.

```
git clone https://github.com/tensorflow/examples
```

Open the TensorFlow source code in Android Studio. To do this, open Android
Studio and select `Open an existing project`, setting the folder to
`examples/lite/examples/image_classification/android`

<img src="images/classifydemo_img1.png?raw=true" />

### Step 2. Build the Android Studio project

Select `Build -> Make Project` and check that the project builds successfully.
You will need Android SDK configured in the settings. You'll need at least SDK
version 23. The `build.gradle` file will prompt you to download any missing
libraries.

#### Switch between inference solutions (Task library vs Support Library)

This Image Classification Android reference app demonstrates two implementation
solutions,
[`lib_task_api`](https://github.com/tensorflow/examples/tree/master/lite/examples/image_classification/android/lib_task_api)
that leverages the out-of-box API from the
[TensorFlow Lite Task Library](https://www.tensorflow.org/lite/inference_with_metadata/task_library/image_classifier),
and
[`lib_support`](https://github.com/tensorflow/examples/tree/master/lite/examples/image_classification/android/lib_support)
that creates the custom inference pipleline using the
[TensorFlow Lite Support Library](https://www.tensorflow.org/lite/inference_with_metadata/lite_support).
You can change the build variant to whichever one you want to build and run—just
go to `Build > Select Build Variant` and select one from the drop-down menu. See
[configure product flavors in Android Studio](https://developer.android.com/studio/build/build-variants#product-flavors)
for more details.

The file `download.gradle` directs gradle to download the two models used in the
example, placing them into `assets`.

<img src="images/classifydemo_img4.png?raw=true" style="width: 40%" />

<img src="images/classifydemo_img2.png?raw=true" style="width: 60%" />

<aside class="note"><b>Note:</b><p>`build.gradle` is configured to use
TensorFlow Lite's nightly build.</p><p>If you see a build error related to
compatibility with Tensorflow Lite's Java API (for example, `method X is
undefined for type Interpreter`), there has likely been a backwards compatible
change to the API. You will need to run `git pull` in the examples repo to
obtain a version that is compatible with the nightly build.</p></aside>

### Step 3. Install and run the app

Connect the Android device to the computer and be sure to approve any ADB
permission prompts that appear on your phone. Select `Run -> Run app.` Select
the deployment target in the connected devices to the device on which the app
will be installed. This will install the app on the device.

<img src="images/classifydemo_img5.png?raw=true" style="width: 60%" />

<img src="images/classifydemo_img6.png?raw=true" style="width: 70%" />

<img src="images/classifydemo_img7.png?raw=true" style="width: 40%" />

<img src="images/classifydemo_img8.png?raw=true" style="width: 80%" />

To test the app, open the app called `VClassify` on your device. When you run
the app the first time, the app will request permission to access the camera.
Re-installing the app may require you to uninstall the previous installations.

## Assets folder

_Do not delete the assets folder content_. If you explicitly deleted the files,
choose `Build -> Rebuild` to re-download the deleted model files into the assets
folder.
