# PointcastSDKPackage

Step 1. Add the PointcastSDK framework to your project.

   To install PointcastSDK package into your packages, add a reference to PointcastSDK and a targeting release version in the dependencies section in Package.swift file:


        import PackageDescription
    	   
         let package = Package(
            name: "YOUR_PROJECT_NAME",
            products: [],
            dependencies: [
                  .package(url: "https://github.com/yellcast/PointcastSDK_iOS.git", from: "0.0.1")
            ]
          )


   <h5>To install PointcastSDK package via Xcode

   Go to File -> Swift Packages -> Add Package Dependency...
   Then search for https://github.com/yellcast/PointcastSDK_iOS.git
   And choose the version you want</h5>

Step 2. Add PointcastSDK in Frameworks, Libraries and Embedded Binaries and choose Embed & Without Sign In option.

Step 3. Import PointcastSDK in ViewController class.

Step 4. Add location privacy permissions to Info.plist

Step 5. Now, add this code in View Controller class

    import UIKit
    import PointcastSDK

    class ViewController: UIViewController {

      let pointcast = PointcastSDK()
      
      override func viewDidLoad() {
          super.viewDidLoad()
       
          pointcast.configure()
          pointcast.closureDidGetAuthorization = { authStatus in
              print("Authorization Status : \(authStatus.rawValue)")
          }
          pointcast.closureDidUpdateBearing = { bearing in
              print("Bearing : \(bearing)")
          }
          pointcast.closureDidGetCoordinates = { coordinates in
              print("Coordinates : \(coordinates)")
          }
          pointcast.closureDidShakeDetected = { detectionStatus in
              print("Detection Status : \(detectionStatus)")
              // None, Sweep, Flick
          }
      }
    }

================== Happy Ending =================
