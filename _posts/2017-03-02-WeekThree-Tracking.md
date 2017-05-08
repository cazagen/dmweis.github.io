---
title: "Week Three: Tracking"
categories: MIX
---

# This weeks topic is Tracking!

Let me start by saying that tracking is my most favorite topic in VR/AR. And when I started writing this post the first time I wrote 700 words of just introduction. I may try to post it as an alternative version but for now here is a very compressed version!

We also didn't do a project this week. At least not entierly. Insted my mobile VR project is a bit of a combination of trackign and mobile. But let me start from the begining. As I said tracking is my favorite topic. And my most favorite trackin system is the Lighthouse tracking system. It was one of the driving reasons for why I bouhgt a vive for mysel. And I have to say that my vive spends most of it's days just laying on my table and plugged in just to work as a reciever for my controllers. Wiritng a simple program that circumvented the entire VR system and just used to controllers as tracking points was actaully one of the first things I did with my vive. And I have since used it for many things ranging from controlling a robotic arm to copy motion of human hand.

let me explain why I love the light house first. The lighhouse system works on a very simple principle taht is based on the system taht is used to navigate plans for landing. Ironically something I alter become very aquinted with when I started workign for Insero Software and was on a team that wrote an application used for testing of just that system.
The lighuse comsists of one/two base stations that have infrared lgiths in them that regularly flash the entire room with infrared light, and than two motors that to a horizontal and vertical sweep with infrared light. Since I am limited on word count I won't go into detail but here is a nice video that exaplins it

<iframe width="560" height="315" src="https://www.youtube.com/embed/J54dotTt7k0" frameborder="0" allowfullscreen></iframe>

One of vives prototypes using fiducial markers for positional tracking:
![Test image]({{site.url}}/images/tracking/Valve_VR_room.png)

```csharp
static void ReadRelativePosition()
      {
         EVRInitError initError = EVRInitError.None;
         CVRSystem cvrSystem = OpenVR.Init(ref initError, EVRApplicationType.VRApplication_Utility);
         Console.WriteLine("Error: " + initError.ToString());
         if (cvrSystem == null)
         {
            Console.WriteLine("Error! evrSystem null!");
         }
         while (true)
         {
            TrackedDevicePose_t[] trackedDevicePose = new TrackedDevicePose_t[OpenVR.k_unMaxTrackedDeviceCount];
            cvrSystem.GetDeviceToAbsoluteTrackingPose(ETrackingUniverseOrigin.TrackingUniverseRawAndUncalibrated, 0f, trackedDevicePose);
            VRControllerState_t controllerState = new VRControllerState_t();
            cvrSystem.GetControllerState(1, ref controllerState, (uint) System.Runtime.InteropServices.Marshal.SizeOf(typeof(VRControllerState_t)));
            bool trigger = controllerState.rAxis1.x > 0.9f;
            bool applicationButton = (controllerState.ulButtonPressed & (1ul << (int)EVRButtonId.k_EButton_ApplicationMenu)) != 0;

            TrackedDevicePose_t pose = trackedDevicePose[1];
            ETrackingResult trackingResult = pose.eTrackingResult;
            HmdMatrix34_t hmdMatrix = pose.mDeviceToAbsoluteTracking;
            Position pos = new Position(hmdMatrix);
            Rotation rot = new Rotation(hmdMatrix);
            Console.WriteLine($"Position: {pos} Rotation: {rot} trigger {trigger} app {applicationButton}");
         }
      }
```

Last build time: {{ site.time }}