<p align="center">
  <img src="http://s23.postimg.org/4psw1dtyj/TGCamera_View_Controller.png" alt="TGCameraViewController" title="TGCameraViewController">
</p>

<p align="center">
  <img src="http://s13.postimg.org/cjxkzgu87/TGCamera_View_Controller.png" alt="TGCameraViewController" title="TGCameraViewController">
</p>

Custom camera with AVFoundation. Beautiful, light and easy to integrate with iOS projects.

[![Build Status](https://api.travis-ci.org/tdginternet/TGCameraViewController.png)](https://api.travis-ci.org/tdginternet/TGCameraViewController.png)&nbsp;
![License MIT](https://go-shields.herokuapp.com/license-MIT-blue.png)&nbsp;
[![Cocoapods](http://img.shields.io/cocoapods/v/TGCameraViewController.svg)](http://cocoapods.org/?q=on%3Aios%20tgcameraviewcontroller)&nbsp;
[![Cocoapods](http://img.shields.io/cocoapods/p/TGCameraViewController.svg)](http://cocoapods.org/?q=on%3Aios%20tgcameraviewcontroller)&nbsp;
[![Analytics](https://ga-beacon.appspot.com/UA-54929747-1/tdginternet/TGCameraViewController/README.md)](https://github.com/igrigorik/ga-beacon)

* Completely custom camera with AVFoundation
* Custom view with camera permission denied
* Easy way to access album (camera roll)
* Flash auto, off and on
* Focus
* Front and back camera
* Preview photo view with three filters (fast processing)
* Visual effects like Instagram iOS app
* Zoom with pinch gesture

<em>This library can be applied on all iPhones and iPods running iOS 7.0+.</em>

---
---

### Adding to your project

[CocoaPods](http://cocoapods.org) is the recommended way to add TGCameraViewController to your project.

* Add a pod entry for TGCameraViewController to your Podfile:

```
pod 'TGCameraViewController'
```

* Install the pod(s) by running:

```
pod install
```

<em>Alternatively you can directly download the [latest code version](https://github.com/tdginternet/TGCameraViewController/archive/master.zip) add  drag and drop all files at <strong>TGCameraViewController</strong> folder onto your project.</em>

---
---

### Usage

#### Take photo

```obj-c
#import "TGCamera.h"
#import "TGCameraNavigationController.h"

@interface TGViewController : UIViewController <TGCameraDelegate>

@property (strong, nonatomic) IBOutlet UIImageView *photoView;
- (IBAction)takePhotoTapped;

@end



@implementation TGViewController

- (void)cameraImage:(UIImage *)image
{
    _photoView.image = image;
    [self dismissViewControllerAnimated:YES completion:nil];
}

- (IBAction)takePhotoTapped
{
    TGCameraNavigationController *navigationController = 
    [TGCameraNavigationController newWithCameraDelegate:self];

    [self presentViewController:navigationController animated:YES completion:nil];
}

@end
```

#### Choose photo

```obj-c
#import "TGAlbum.h"

@interface TGViewController : UIViewController 
<UINavigationControllerDelegate, UIImagePickerControllerDelegate>

@property (strong, nonatomic) IBOutlet UIImageView *photoView;
- (IBAction)chooseExistingPhotoTapped;

@end



@implementation TGViewController

- (void)imagePickerController:(UIImagePickerController *)picker 
didFinishPickingMediaWithInfo:(NSDictionary *)info
{
    _photoView.image = [TGAlbum imageWithMediaInfo:info];
    [self dismissViewControllerAnimated:YES completion:nil];
}

- (void)imagePickerControllerDidCancel:(UIImagePickerController *)picker
{
    [self dismissViewControllerAnimated:YES completion:nil];
}

- (IBAction)chooseExistingPhotoTapped
{
    UIImagePickerController *pickerController = 
    [TGAlbum imagePickerControllerWithDelegate:self];

    [self presentViewController:pickerController animated:YES completion:nil];
}

@end
```

---
---

### Requirements

TGCameraViewController works on iOS 7.0+ version and is compatible with ARC projects. It depends on the following Apple frameworks, which should already be included with most Xcode templates:

* AssetsLibrary.framework
* AVFoundation.framework
* CoreImage.framework
* Foundation.framework
* MobileCoreServices.framework
* UIKit.framework

You will need LLVM 3.0 or later in order to build TGCameraViewController.

---
---

### Todo

* Customize layout programatically
* iPad support
* Preview when user choose photo 

---
---

### License

This code is distributed under the terms and conditions of the [MIT license](LICENSE).

---
---

### Change-log

A brief summary of each TGCameraViewController release can be found on the [releases](https://github.com/tdginternet/TGCameraViewController/releases).
