+	[Godot XR Projects](#godot-xr-projects)
	+	[Toolkits](#toolkits)
	+	[Examples](#examples)
	+	[Demos](#demos)
	+	[Games](#games)
	+	[Ports](#ports)
	+	[Unsure Source](#unsure-source)

#Godot XR Projects
List of various Godot projects that utilize the older VR or newer XR addon.

---

##Toolkits
1.	**Godot XR Tools**
	-.	Source:	https://github.com/GodotVR/godot-xr-tools
	-.	Info:	Support scenes for AR and VR in Godot
	+	This repository contains a number of support files and support scenes that can be used together with the various AR and VR interfaces for the Godot game engine.
	+	Versions
		+	Official releases are tagged and can be found here.
		+	The following branches are in active development:
			+	Branch 	Description
			+	master 	Godot 3 development branch
			+	4.0-dev 	Godot 4 development branch
	+	How to Use
		+	Information about how to use this plugin can be found in our WIKI.
	+	Preventing hickups
		+	As many of the functions in this module will hide objects that are later shown as the user performs actions, the user will experience a hickup as Godot compiles the shader used to draw the object on screen.
		+	To combat this you will find a scene in this module called misc/VR_Common_Shader_Cache.tscn. Add this scene as a child node to your ARVRCamera. This will trigger the required shaders being compiled the first time your main scene loads.

1.	**Godot XR Tools Demo**
	-.	Source:	https://github.com/Malcolmnixon/godot-xr-tools-demo
	-.	Info:	Demo project for Godot XR tools mechanics
	+	Overview
		+	This is a demo project to show off different godot-xr-tools movement mechanics.
	+	Teleport Demo
		+	The demos/demo-teleport/DemoTeleport scene demonstrates using teleport mechanics to move around the map.
		+	The associated README.md contains the overview of creating the teleport player.
	+	Flying Demo
		+	The demos/demo-flying/DemoFlying scene demonstrates support for flying. It introduces a physics body to the player to ensure the player cannot fly through physical structures.
		+	The associated README.md contains the overview of creating the player with basic direct movement and flying support.
	+	All Demo
		+	The demos/demo-all/DemoAll scene demonstrates support for all of the movement mechanics, specifically:
			+	Direct movement (including strafing)
			+	Jumping
			+	Climbing
			+	Gliding
			+	Wind blown
		+	The associated README.md contains the overview of creating the player with all these mechanics.
	+	The map contains numerous objects to test out the different mechanics, including:
		+	An ice-rink with low traction
		+	A jump spot which greatly enhances the players jump height
		+	Three wind areas that can blow the player along the ground or up into the air


1.	**Godot_XR_Networking-Plus-Game**
	-.	Source:	https://github.com/teddybear082/Godot_XR_Networking-Plus-Game
	-.	Info:	A test of Godot, networking, XR-tools modifications and Pac-Man style gameplay
	+	INSTALLATION
		+	Quest native - download APK and signature file to your hard drive, use sidequest's feature to install a local APK to your quest by selecting the files
		+	PCVR/OpenXR - download the zip and unzip the directory anywhere. Run the .exe file. Your VR Software should boot up and start you in the game. In theory, should work with all VR headsets; tested with Quest / Virtual Desktop. You need a PCVR-ready PC.
		+	If you use Virtual Desktop, make sure you have SteamVR set as your OpenXR runtime.
	+	MULTI-PLAYER (Experimental, and see "Known Issues" at bottom)
		+	Once you get into the "real game" you can see a networking debug menu in front of you. You can hide it or bring it up again by pressing the left controller Y button.
		+	If you have two headsets you can play local multiplayer by going to the top left drop down menu and choosing "ENet" and going to the top right menu and choosing one person "as server" and the other person as "Local Network."
		+	In theory, both of you should then connect to the game together.
		+	If you want to play with someone online, keep the network option in the top left corner at its default (WebRTC/MQTT) and in the top right corner both choose "as necessary." In theory one person should be assigned automatically as the server and the other as the client and connect.
		+	There's only been very limited testing on this, and objects/ghosts do not sync, only the other player's avatars. So for now, think of it like you are in parallel universes with a bridge between you...


1.	**Godot VR Physics Template**
	-.	Source:	https://github.com/jtnicholl/godot3-vr-physics-template
	-.	Info:	Basic template for VR applications in Godot with physics interactions
	+	This is a basic template for a VR application in Godot with physical hands that interact with the environment, and cannot go through walls or other solid objects. The player can pick up items, and those too cannot be pushed through walls. It also provides other expected VR functionality such as turning and teleporting, as well as some other basic features for any application including loading settings at runtime from a config file.
	+	Godot version 3.5 or later is required, this is because 3.5 introduced asynchronous shader compilation and shader caching. This prevents stuttering caused by shader compilation, which is a nuisance in normal desktop games but in VR it is severely nausea inducing.
	+	Godot 4.0 is not supported. I intend to port this to 4.0 using its built-in OpenXR support in a separate repo later.
	+	Why should I use this?
		+	Many VR games use a very simple system for the player's hands. The hand copies the position of the controller every frame, and that's it. When the player picks up an object with their hand, the object gets its physics shut off, and it gets dragged along with the hand. When the item is let go it is disconnected from the controller, its physics turned back on, and sometimes it is given an impulse so it can be thrown.
		+	This is the system used by all VR Godot projects I could find online. Its obvious limitation being that the player's hands and any objects they pick up simply phase through walls with no collision.
	+	New method
		+	This template takes a different approach to hands. For each hand it involves:
			+	The ARVRController node built into Godot. This copies the position of the controller.
			+	A "hand anchor," which is a KinematicBody with a small shpere shape. It uses move_and_slide to copy the position of the controller, but without passing through the environment.
			+	A hand node, which is a RigidBody that uses _integrate_forces to losely copy the rotation of the controller. This is also where the hand is visually displayed.
			+	A PinJoint node that moves the hand node to the hand anchor node. Since the hand anchor won't pass through walls, this is never too extreme of a force.
		+	For picking up an object, the hand node moves to the nearest grabbable point on the pickup and then the pickup is reparented to the hand. However, instead of just disabling collision on the picked up object, its collision bounds also get reparented to the hand. This effectively turns the object into an extension of the hand's collision bounds, keeping them together while also preventing them from passing through walls.

1.	**Mixed Reality Extension SDK Godot**
	-.	Source:	https://github.com/dasg34/mixed-reality-extension-godot
	-.	Website:	
	-.	Info:	The Mixed Reality Extension Godot library is an easy way for developers to add User Generated Content (UGC) capabilities to their GodotEngine-based host apps
	+	The Mixed Reality Extension SDK Godot library makes it easy for any Godot app or game to support user generated content (UGC) built with the Mixed Reality Extension SDK. It also makes it easy to test an MRE within a simple environment inside the Godot editor.
	+	This project was forked from [Mixed Reality Extension Unity](https://github.com/Microsoft/mixed-reality-extension-unity).
	+	Prerequisites
		+	Install Git
		+	Use [GodotEngine](https://godotengine.org/) to Install Godot 3.
	+	How to build and run Hello World in the Godot editor
	+	From command prompt:
		+	git clone http://github.com/dasg34/mixed-reality-extension-godot
		+	Open Godot editor with project.godot
		+	Open the scene MREGodotRuntime/Scenes/HelloWorld.tscn
		+	Play Scene(F6)
	+	You should now see a slowly spinning Hello World label.
	+	Scene Descriptions
	+	The MRETestbed project contains 4 Godot scenes set up for different testing purposes
		+	HelloWorld.tscn: Connects to a single MRE in the cloud on startup, no interaction needed.
		+	Standalone.tscn: Connects to a localhost.
		+	TriggerVolumeTestBed-localhost.tscn: Connects to a localhost MRE when you walk close - useful for testing user join/leave.
		+	SynchronizationTest-localhost.tscn: Connects twice to twice to a localhost MREs with the same session ID. When you click on the two spheres you will see 2 different connections to the same server, so you can perform basic multiuser testing without multiple machines or multiple unity instances.
	+	The Localhost samples requires a local node server running, see the [Sample repository](https://github.com/Microsoft/mixed-reality-extension-sdk-samples#How-to-Build-and-Run-the-Hello-World-sample) for localhost deployment.
	+	Overview
		+	For more information, please see the [Mixed Reality Extension SDK](https://github.com/Microsoft/mixed-reality-extension-sdk) repository's [README.md](https://github.com/Microsoft/mixed-reality-extension-sdk/blob/master/README.md) is the best source of information about features, current state, limitations, goal, major known issues, and roadmap.

1.	**Godot-OpenVR-Controller-Template**
	-.	Source:	https://github.com/Groguard/Godot-OpenVR-Controller-Template
	-.	Info:	A basic Godot OpenVR controller template
	+	A basic Godot OpenVR controller template This was built using Godot 3.2 and the latest openvr addon from the assests library. I've made a few modifications to the default helper scenes to make some of the features in this demo work. If you update the scripts in this project, it will break.
	+	Current Features
		+	Picking up and dropping objects
		+	Climbable objects
		+	Object tool belt
		+	Basic Smooth locomotion
		+	Actions
	+	Planned Features
		+	Teleport movement
	+	Known Issues
		+	Can't walk up slopes

1.	**Godot Oculus Quest Toolkit**
	-.	Source:	https://github.com/NeoSpark314/godot_oculus_quest_toolkit
	-.	Info:	An easy to use VR toolkit for Oculus Quest development using the Godot game engine
	+	Features
		+	Touch controller button handling and controller models
		+	2D UI canvas with controller interaction and Virtual Keyboard
		+	Joystick locomotion and rotation (smooth and step)
		+	Rigid body grab
		+	Basic Player Collision
		+	Falling and Climbing logic
		+	Oculus Mixed Reality Capture Integration
		+	Hand Tracking support with included hand models and basic gesture detection
		+	VR Simulator and VR Recorder (for easier testing on desktop)
		+	Several utilities to accelerate prototyping and debugging (Log, Labels, ...)
		+	Jog in Place detection

1.	**Godot VR Toolkit**
	-.	Source:	https://github.com/boku-ilen/godot-vr-toolkit
	-.	Info:	A few useful nodes that should ease implementing VR in Godot. UI, Teleport and other useful tools.
	+	VR-Locomotion using a efficent way for intuitive teleportation
	+	Object-Interaction System
		+	A superclass that is base on a rigidbody and can be extended, like described in the tutorial of https://github.com/GodotVR/godot_openvr_fps
		+	A compass, a simple ball, aswell as a pew-pew-gun system are currently implemented to show the usage of this system, more will follow
		+	It is possible to throw the objects in the direction of the controller-motion
	+	Easily render a viewport on a plane (in the future probably also more complex shape) so you can create user interfaces
		+	This includes rendering of UI-Scenes aswell as cameras
		+	The project has two testing scenes for this (UI and a camera)
	+	VR-Controller UI Interaction
		+	Like in common VR-projects and menus, a RayCast is sent from the controller which collides with a viewport on a mesh
		+	With a faked InputEventMouse interaction with those viewports can be "faked": InputEventMouse
		+	Vibration in the controller on hovering UI-elements

1.	**Godot OpenVR FPS**
	-.	Source:	https://github.com/GodotVR/godot_openvr_fps
	-.	Info:	Repository for the OpenVR starter tutorial
	+	The tutorial covers how to create a first person shooter (FPS) VR game in Godot using GDscript. The project on this repository is the finished result of the Godot tutorial.
	+	Safety notice
	+	Virtual Reality (VR) can cause seizures, discomfort, and other problems for some individuals. Take breaks when required and follow the health and safety warnings for your Virtual Reality headset!
	+	Project Features
		+	VR locomotion through teleportation and artificial movement.
			+	Point and teleport locomotion by pressing the trigger while not holding any objects. This locomotion snaps the player instantly to the new position.
			+	Artificial movement locomotion by moving the VR joystick and/or touch-pad. This locomotion 'moves' the player through 3D space, applying a slight vignette to reduce motion sickness.
		+	A RigidBody-based 3D object interaction system that uses the VR controllers.
			+	Pick up, drop, and throw both normally RigidBody and Rigidbody-derived nodes.
			+	Pick up objects using either with an Area node or a Raycast node.
		+	Interact with specially coded RigidBody-based objects.
			+	Currently the project has: pistols, a shotgun, a sword, and some simple bombs.
			+	There are simple targets that break into pieces when damaged.
		+	3D UI with in-game instructions.
		+	The project should work with all major VR headsets.
		+	And more!

1.	**Godot XR Interaction Helpers**
	-.	Source:	https://github.com/balintmaci/Godot-XR-Interaction-Helpers
	-.	Info:	Plug-and-Play XR features
	+	This addon contains helper classes and example scenes for common XR related challenges. Currently it supports movement with or without collisions and physics, rotation of player around camera, setting orientation intuitively based on a combination of head orientation and hands position. Future version will add grab, touch, climbing, space physics, etc.
	+	Dependencies:
		+	Extra Math for GDScript
		+	some kind of VR runtime, such as OpenXR
	+	Ensure that the InputMapper script in the autoload folder has been activated in the project settings as an AutoLoad
	+	Check the examples folder for inspiration on how to use the scripts in this addon to build your VR scene.
	+	Feature Nodes
		+	ReferenceOffsetCompensatingRotator
		+	FreeLookMover
		+	FlatWorldPhysicsKinematicMover
		+	TripleMethodOrientationGuesser
		+	VrFrameHeightScaler
		+	Other Classes
		+	ArvrOriginWithReferences
		+	BaseMapping
		+	InputMapper
		+	SpatialManipulator, KinematicBodyManipulator
		+	ArvrManipulator

---

##Examples
1.	**Godot XR Tools Experiments**
	-.	Source:	https://github.com/Malcolmnixon/godot-xr-tools-experiments
	-.	Info:	Experimental Project to evaluate and evolve new functionality for godot-xr-tools
	+	This repository contains a number of experimental scripts to evaluate functionality destined for the godot-xr-tools project.
	+	Experiments
		+	The following experiments are being evaluated before migration:
			+	Generic View Fader
			+	Fading based on request (E.G. around scene transitions)
			+	Fading based on collisions (E.G. to prevent looking through walls)

1.	**godot-xr-virtual-keyboard-demo**
	-.	Source:	https://github.com/Malcolmnixon/godot-xr-virtual-keyboard-demo
	-.	Info:	Demo project showing of the experimental godot-xr-tools virtual keyboard

1.	**godot-xr-doors**
	-.	Source:	https://github.com/Malcolmnixon/godot-xr-doors
	-.	Info:	Proposal for godot door mechanics

1.	**Godot_XR_networking-modular**
	-.	Source:	https://github.com/teddybear082/Godot_XR_networking-modular
	-.	Info:	Attempt at modular version of Godot_XR_networking by GoatChurchPrime
	+	Attempt at modular (tool) version of Godot_XR_networking by GoatChurchPrime: https://github.com/goatchurchprime/Godot_XR_networking to insert into your OpenXR project.
	+	This is a tempoarary repository, for review by GoatChurchPrime. If it works, any future work will be done on his repository, not this one.
	+	This is a minimal working VR networking module using the https://github.com/goatchurchprime/godot_multiplayer_networking_workbench as the basis for connecting using one of the three godot networking protocols (enet, websocket or webrtc) and spawning player avatars into the space on connection. This works in Godot 3.4., and works with projects built for PCVR as well as Quest native.
	+	It requires installation first of the OpenXR Asset Plugin and OpenXR-Tools asset plugin as described below into your project.

1.	**Godot_XR_Tools_Bullet_Time**
	-.	Source:	https://github.com/teddybear082/Godot_XR_Tools_Bullet_Time
	-.	Info:	Provides slo-mo movement to player

1.	**Godot_XR_JogInPlace_Locomotion**
	-.	Source:	https://github.com/teddybear082/Godot_XR_JogInPlace_Locomotion
	-.	Info:	Attempt at porting NeoSpark's Walk in Place Locomotion for use in Godot XR-Tools

1.	**Godot XR Reference plugin**
	-.	Source:	https://github.com/GodotVR/godot_xr_reference
	-.	Info:	Reference implementation for Godot 4 XR plugins
	+	This is a reference plugin to use as a base to implement XR plugins for Godot 4 and later.
	+	This is a Work In Progress.

1.	**VR Mobile Camera**
	-.	Source:	https://github.com/OfficinePixel/vr_mobile_camera
	-.	Website:	http://www.officinepixel.com/
	-.	Info:	VR Camera for mobile headset/cardboard VR
	+	VR Mobile Camera
		+	This node plug-in for Gotot Engine enable a new kind of 3D camera, you can use it with phone vr headset or cardboard.
		+	It provide screen split for stereoscopic vision and head tracking by using accelerometer and gyroscope sensor on the phone, if gyroscope is not found, magnetometer will be used as fall back.
		+	Gyroscope data are matched with accelerometer data so to have a very accurate and responsive tracking, unfortunately only hi-end phones provide gyroscope, so, magnetometer is supported too.
		+	Magnetometer outputs a very noisy data, so, the signal is filtered in order to make it usable. The drawback of filtering data is that you introduce a lag. You can balance noise and lag by modifying the Magnetometer Interpolation parameter in the camera inspector.
	+	VR Camera Parameters
		+	You can set some camera parameter in the inspector panel inside Godot.
		+	You can set Eyes Distance and Eyes Convergence.
		+	The camera can moves on the plane if you push the visor up and down, the speed is set by the Walking Speed parameter.
		+	Fow, Near and Far just work as on regular 3D camera.
		+	Magnetometer Interpolation sets the number of frames to be taken in count for interpolating data, the higher is the number the smoother is the view but increments the lag.
		+	You can lock an axis rotation by unchecking Enable Yaw, Enable Pitchand Enable Roll.
		+	Show Data check showd sensors data during runtime and is mainly for debugging purposes.
	+	Interactive Objects
		+	Often user using HMD have no input devices for interacting with application, for this reason I've introduced interactive objects.
		+	An Interactive object reacts when it's in the center of the view, a progress circle is shown, so, you have the time of moving your view away from it if you don't really wish interacting to it, otherwise, if you hold it at the center for a while you trigger the action on it.
		+	Take a look to test_scene.tscn for an example on how it works.
		+	In a few words you have to setup a collision object and then attach a script to it. The script have to contains _on_action() function containing the code to execute when the object is triggered by the user and, optionally, a _on_roll_in() / _on_roll_out() function if you wish give some feedback.
		+	#Compatibility The plug in was tested successfully on Android devices.
		+	There is initial iOS support but it seems Godot can't access magnometer and gyroscope data on such OS so it's not very usefull on Apple devices right now.
		Fortunately Bastiaan Olij is working on Godot sources for implementing them.

1.	**VR Streaming Overlay**
	-.	Source:	https://github.com/beniwtv/vr-streaming-overlay
	-.	Info:	SteamVR overlay for streamers on Linux/Windows
	+	This is a SteamVR overlay for streamers on Linux/Windows. (Made using the awesome Godot game engine ;)
	+	Note: The master on this repository is kept roughly in sync with Godot / Godot OpenVR master. For official releases of Godot please check the releases page and/or the respective branches.
	+	Note: While this is also compiled for Windows at the moment, this is currently untested. Feedback is welcome here :)
	+	Also note this is in an early state, but testers/feedback are welcome of course!
	+	Current features:
		+	Should support all SteamVR-supported headsets (only HTC Vive/Valve Index tested though - feedback welcome)
		+	Adjustable background opacity and color
		+	Adjustable overlay size in the VR world
		+	Shows Twitch chat
		+	Track overlay with left/right hand
		+	Configurable position and rotation relative to tracking device or absolute in VR world
		+	Configurable widget system to show different things - like Twitch chat and Twitch stats (followers, current viewers, alerts...)
		+	Trigger gesture to show/hide overlay (attached left/right hand)

1.	**OVR Utils**
	-.	Source:	https://github.com/CrispyPin/ovr-utils
	-.	Info:	Overlay app for OpenVR/SteamVR on Linux/Windows made in Godot
	+	A cross-platform SteamVR overlay application that aims to have many useful tools available while in VR. Built using the Godot game engine, and the godot-openvr plugin to interact with the openvr SDK.
	+	Installation
		+	Grab the latest release for your OS from the releases section
		+	Extract the contents to somewhere (make sure to mark ovr-utils-linux-v###.x86_64 as executable on linux)
		+	To start the overlay, just run the .exe or .x86_64 file.
	+	Add to steam (optional)
		+	In steam, go to Games>Add a non-steam game to my library
		+	Click browse and find the ovr-utils executable
		+	Click add and then add selected programs
		+	You should now be able to start it from steam (favourite it for easier access)
	+	Usage
	+	At the moment all interacions are done with the trigger buttons, this will use steamvr actions and be configurable in the future.

1.	**Godot experiments**
	-.	Source:	https://github.com/MrEliptik/godot_experiments
	-.	Website:	https://mreliptik.carrd.co/
	-.	Info:	Some 2D, 3D & VR experiments and tutorials in Godot 3
	|  Type   |  Title | Description | Status |
	:-----:|:-------:|:-------:|:-----------:|:------:|
	|  VR | quest_playground | a project testing various things in VR for the Oculus Quest: handtracking, handtrackings physics | WIP 🛠
	|  VR | table_tennis | trying to use Godot's physic to recreate a table tennis game | WIP 🛠
	|  VR | bow_and_arrow | bow and arrow mechanic | WIP 🛠
	|  VR | control_like_interaction | trying to recreate CONTROL like movement, and messing with area's gravity | DONE ✔

1.	**GUI in VR in Godot**
	-.	Source:	https://github.com/aaronfranke/godot-GUI-in-VR
	-.	Info:
	+	Check this out on the Godot Asset Library: https://godotengine.org/asset-library/asset/900
	+	Check out the demo on the Godot Asset Library: https://godotengine.org/asset-library/asset/604
	+	Video demo: https://www.youtube.com/watch?v=Xrhje9RwLnU (this repo does not include the skybox)

1.	**3DTV Module**
	-.	Source:	https://github.com/BastiaanOlij/godot_3dtv
	-.	Info:	Using the ARVR server implementation to implement support for 3D TVs and 3D monitors
	+	This GDNative module uses the AR/VR system to implement a stereo scopic camera setup that can be used for 3D TVs and 3D monitors. Currently it only supports side by side splitscreen.
	+	Compiling this project
		+	This module is dependent on godot-headers. Before compiling make sure it has been downloaded. If the godot_headers folder is empty the easiest way to do so is to run the following commands:
			+	git submodule init
			+	git submodule update --recursive
			+	Now compile this module:
			+	scons platform=windows target=release
			+	(change platform to linux or osx if appropriate)

1.	**DurielsGodotUtilities**
	-.	Source:	https://github.com/TheDuriel/DurielsGodotUtilities
	-.	Website:	https://twitter.com/the_duriel
	-.	Info:	A collection of useful Scripts, Scenes, Systems, and Templates for the Godot Game Engine.
	+	All content is MIT.
	+	Like the content? Follow me on Twitter https://twitter.com/the_duriel or support my Patreon https://www.patreon.com/TheDuriel
		+	`Classes/`, Standalone Classes of various nature.
		+	`UIComponents/`, Individual Control classes or entire Scenes.
		+	`UtilityAI-Static/`, the Core components of a Utility based AI model.
		+	`VR/` VR specific Classes and Scenes.
		+	`addons/` Editor Plugins.
		+	`addonsbasic/` More complex systems which use class_name to add themselves to your editor.
		+	`outdated/` Code examples and older work which may no longer function.
	+	Some highlights:
		+	`.gitignore` and `.gitattributes` covering many standard file formats and conventions relating to Godot.
		+	`addons/DurielEditorTools` adds some minor, yet useful enhancements, to the Editor. Including enhanced performance when running your game, (by switching to the script view, and optionally preventing the editor from rendering in the background), and setting a fixed minimum size to all Docks. It also hides the Asset library button.
		+	`addonsbasic/AutoAstar2D` is an Astar2D wrapper which allows you to visually build A* grids from within the editor. The grid can be updated in _real time_, even during gameplay. https://twitter.com/the_duriel/status/1248239309116899328
		+	`addonsbasic/StateMachine` is a fully code based StateMachine implementation. Including Master state, State Switching, Entry and Exit events, ~~and Pushdown Automata.~~
		+	`addonsbasic/UserOptions` is a Singleton which abstracts saving and loading user options from a .cfg file, boiling it all down to single function calls. It also autosaves the settings.
		+	`addonsbasic/VRUI` is a UI in 3D implementation which allows interaction through mouse, and a virtual mouse pointer (raycast) for VR usage.

1.	**LensDistortion**
	-.	Source:	https://github.com/BastiaanOlij/LensDistortion
	-.	Info:	Example for applying a lens distortion shader in Godot for Mobile VR
	+	Example for applying a lens distortion shader in Godot for Mobile VR
	+	You can copy the files in Cameras into your own project to use the setup. This handles rendering two cameras to the correct viewports and handles preparing a distortion map to apply the lens effect.
	+	The objects displayed in this demo scene are too close and you're eyes will probably hurt if you put this on.
	+	I'm still working on a settings window that allows you to enter the variables that control how things are rendered. I'll see if I can put a list together of common phones and headset. The information is readily available but a bit of a pain. The current settings in the project are for an iPhone 7, if you've got a cardboard type viewer the lens constants are probably too high. 
	+	Note that for this to work you need the frustum mode enhancement to Godot:
		+	Godot 2.x: https://github.com/godotengine/godot/pull/7778
		+	Godot 3.x: https://github.com/godotengine/godot/pull/7121

1.	**godot-xr-hands-on**
	-.	Source:	https://github.com/Jade1724/godot-xr-hands-on
	-.	Info:	My first Godot XR hands on project
	+	To run this project, download it and install OpenXR Plugin locally on your machine.

---

##Demos
1.	**Godot 4 OpenXR demo project**
	-.	Source:	https://github.com/BastiaanOlij/godot4_openxr_demo
	-.	Info:	Crappy test project to test Godot 4s OpenXR implementation with
	+	What you are looking at is my absolutely crappy demo project for testing the OpenXR logic we're porting into Godot 4 core. Maybe one day it will evolve into a proper demo project (thats the hope). Contributions super welcome.
	+	Use in combination with godotengine/godot#56394

1.	**Godot VR Weapons demo**
	-.	Source:	https://github.com/BastiaanOlij/godot-vr-weapons
	-.	Info:	Supporting project for my vr weapons tutorial
	+	This is a Godot demo project in support of my Godot VR weapons youtube tutorial videos: [Playlist)(https://www.youtube.com/playlist?list=PLe63S5Eft1KaIq9N5PsS5FA3pcLrh686y)
	+	In order to run this project you will Godot 3.2 or later. It can be adopted to 3.1 with minor changes especially around the shaders.
	+	Included in this repository is a custom windows build of the Godot OpenVR plugin with PR #30 applied. If you wish to run this project on another OS please compile from source code found here: https://github.com/GodotVR/godot_openvr
	+	This repository also includes a copy of https://github.com/GodotVR/godot-xr-tools (formally vr-common).

1.	**Godot Object Interaction in VR**
	-.	Source:	https://github.com/BastiaanOlij/godot-object-interaction-vr
	-.	Info:	Support files for my Object Interaction VR tutorial series
	+	This repository contains the source code of the demo project used for the Object Interaction in VR tutorial series I have on my Youtube channel.
	+	You can find those here:
		+	[Part one](https://youtu.be/o6GIoO97vGQ)
		+	[Part two](https://youtu.be/8yI05GVuQck)

1.	**sandboxVR**
	-.	Source:	https://github.com/the-dev-bin/sandboxVR
	-.	Info:	
	+	Update
		+	This project is currently no longer being maintained as of 10/19/2020. The use of Godot engine for VR proved to be underwhelming and may be revisited at a later date.
		+	This is a project for a hackathon, to build a sort of Gary's mod but for VR. The idea is this stands as a framework for building loadable mods. The major goals of this project were to offer an engine for VR dev that skips the need to worry about movement, and interaction with objects. This project as mentioned in the section below takes advantage of the Godot OpenVR module as the primary engine to allow for cross-platform capabilities.
	+	So Far
		+	We have worked out the basics of movement and teleportation in VR. We have added some basic examples of scenes that could be added in. We have implemented a simple drawing mod as well as a sword that has collision on.
	+	Known Issues
		+	The primary issue is dealing with dynamic loading in the world. We wanted to have a GUI typer interface that loads on your left hand and you can select some mod to load in. There are some technical challenges when doing so. It has been scrapped while we need to learn more about how to make dynamic loading.
	+	Painter
		+	The painter modules use the Immediate Geometry of Godot to build an array of v3 points and then draw them as a single line.
		+	Goals
			+	The painter could use new textures instead of the base texture, as well as the ability to select color and thickness.
		+	Known Issues
			+	No way to undo what you have drawn, can't stop once you start drawing.
	+	Sword
		+	The sword scene is based on a free sword skin and has collision features added to it.
		+	Goals
			+	The sword needs to have a better grab point so it is not in the middle of the sword

1.	**Simula**
	-.	Source:	https://github.com/SimulaVR/Simula
	-.	Website:	https://simulavr.com/
	-.	Info:	Linux VR Desktop
	+	[Simula](https://simulavr.com) is a VR window manager for Linux that runs on top of [Godot](https://godotengine.org/). It takes less than 1 minute to install.
	+	*Video:* [Demonstration.](http://www.youtube.com/watch?v=FWLuwG91HnI)
	+	*Compatibility:* Simula is officially compatible with SteamVR headsets equipped with Linux drivers (e.g. HTC Vive, HTC Vive Pro, & Valve Index).  We have also added experimental support to OpenXR headsets that have Monado drivers (e.g. North Star, OSVR HDK, and PSVR).  Some people have gotten the Oculus Rift S to run Simula via OpenHMD (see [here](https://github.com/OpenHMD/OpenHMD/issues/225#issuecomment-638454156)), though we have not officially tested this ourselves.
	+	*Mission:* Facilitate a Linux future for VR & AR Desktop. In the short-run, this means allowing people to run 2D Linux apps with current generation headsets. In the long-run, this means allowing people to run Linux in standalone AR & VR HMDs.
	+	*Simula One Headset:* We are also in the process of developing a (limited number of) portable VR headsets for sale which come with SimulaVR mounted on them by default.  If you are interested in purchasing one, [visit our website](https://simulavr.com) and join our waitlist to receive a place in line and/or periodic updates on its development.
	+	*Origins:* Simula is a reimplementation fork of [motorcar](https://github.com/evil0sheep/motorcar). To read about motorcar, see *[Toward General Purpose 3D User Interfaces: Extending Windowing Systems to Three Dimensions](https://github.com/evil0sheep/MastersThesis/blob/master/thesis.pdf?raw=true)*

1.	**PrinterfaceVR**
	-.	Source:	https://github.com/FabLabSiegen/PrinterfaceVR
	-.	Info:	A simple VR Interface in Godot for Prusa MK3 Printer over Octoprint
	+	The VR Part of this Project is copied and pasted from 3 Projects to test my Octoprint Interface in VR combining two of the most exciting new technologies of the second decade of the 21 Century in an so far utterly useless but i.m.O. funny Fashion
	+	The base Construct of the VR implementation is a bold copy from Bastiaan Olij's OpenVR Test scene for the Godot gameengine https://github.com/BastiaanOlij/godot_openvr
	+	The 3D Printer is a lower-poly copy of the complete Prusa3d CAD model from jzkmath https://github.com/jzkmath/Original-Prusa-i3/tree/MK3
	+	The Octoprint interface dll is a version of my C# Interface for Octoprint Printerface https://github.com/FabLabSiegen/Printerface/tree/master/Printerface
	+	The Project can be edited with Godotengine Version 3.1 with Mono support (Mono Version 5.12, no later, no earlier, only 5.12 works), i'm currently using Alpha 2 if you want to use this productively i'd reccommend copying most into a Version of BastianOlij's godot_openvr Project that uses a stable Godotengine Version.
	+	Following are the usual instructions from BastianOlij's godot_openvr Test scene, as they apply to this Scene as well.

---

##Games
1.	**VRWorkout**
	-.	Source:	https://github.com/mgschwan/VRWorkout
	-.	Website:	https://vrworkout.at/
	-.	Info:	High-intensity virtual reality workout game
	+	A virtual reality music workout game built with Godot Engine
	+	The game sould be a physically engaging VR experience that is somewhat comparable to a short calisthenics workout (or a long one if you play for extended periods). Compared to other music games like Beat Saber and Box VR there should be more muscle groups activated due to the changes between standing, squatting, pushups, side planks, crunches, jumping and burpees.
	+	But as with all games it is up to the player to actually work out and not cheat it's way through the movements. The only opponent in this game is the players body itself, if you really engage in it you will feel the exertion it brings with it.
	+	Positions:
		+	Standing (or running to get point multipliers)
		+	Jumping. To reach the head cues the player will need to jump a bit
		+	Squatting. The game will require deep squats
		+	Crunches. You don't need to do repetitive crunches but be on your back and try to hit the head and double hand cues
		+	Pushups. Try to hit the hand cues while in the pushup position (one handed punches will activate your core muscles). The head cues will drive your movement up and down
		+	Burpees. Hit the head cues in the pushup position then immediately jump up to hit the head cue in the jump position.
	+	The game switches between those four positions to avoid a monotone workout.
	+	DISCLAIMER: Use at your own risk! This game does not check if you bump into your surroundings. Since this is a physical workout game there is lot's of movement which bears the risk of injury. You acknowledge that this software is free and you are using it at your own risk

1.	**Scalhaven**
	-.	Source:	https://github.com/MagniGames/Scalhaven
	-.	Info:	Rogue-like VR FPS with a Steampunk style
	+	This project is meant to be imported in Godot 3.0 in order to function. The .gd scripts can be opened in any text editor.
	+	Prerequisites
		+	Godot 3.0

1.	**Bike-Game**
	-.	Source:	https://github.com/Faymoon/Bike-Game
	-.	Website:	
	-.	Info:	Little VR bike game with Godot Engine
	+	Build
		+	Follow this [tutorial](https://docs.godotengine.org/en/stable/getting_started/workflow/export/android_custom_build.html#doc-android-custom-build) of the godot engine documentation.
	+	VR setup
		+	If you have a cardboard-like VR headset this game should work for it, in order to have an optimal experience consider modifying the `MobileVRInterface`'s parameters in [src/Game.cs](https://github.com/Faymoon/Bike-Game/blob/master/src/Game.cs#L54).
	+	For cardboard compatible headset
		1.	Scan your device's QR Code with a small cardboard logo in. You'll get a link with base 64 encoded data after the `p=`. 
		1.	To decode this data you need [protoc](https://github.com/protocolbuffers/protobuf/releases) (download just the protoc-\<version\>-*.zip if you don't need to compile it yourself). 
		1.	You'll also need the protocol description file, for google cardboard data you can find it [here](https://github.com/google/wwgc/blob/master/www/CardboardDevice.proto).
		1.	`$ echo <insert your base 64 encoded data here> > encoded`
			+	This data should look something like this : `ChJULlQuIEludGVybmF0aW9uYWwSEzNEIFZSIFZpZXdlciBEZWx1eGUdJQaBPSUK1yM9KhAAAEhCAABIQgAASEIAAEhCWAE1KVwPPToICtcjPArXIzxQAWAB`
		1.	`$ base64 -d encoded > data` This command converts the base 64 data to raw data.
		1.	`protoc --decode=DeviceParams CardboardDevice.proto < data` This command decodes the raw data to give you the wanted values and prints them into std out.
	+	Then you can change the data in the code (don't forget that units can be differents)
	+	GodotBluetooth
		+	I use a modified version of this [project](https://github.com/favarete/GodotBluetooth) which is under MIT license. I made a few changes in order to make it working with my project/Godot 3.2 and to debug. 

1.	**Friday Night Funkin' VR**
	-.	Source:	https://github.com/this-is-bennyk/Funkin-VR
	-.	Website:	https://thisisbennyk.itch.io/funkin-vr
	-.	Info:	Fanmade VR port of Friday Night Funkin'
	+	What the funk is this?
		+	Friday Night Funkin' VR (FNFVR for short) is a unofficial / fanmade standalone VR port of Friday Night Funkin' (FNF), a rhythm game originally created for Ludum Dare 47 "Stuck in a Loop".
		+	You can find the original FNF on [itch.io](https://ninja-muffin24.itch.io/funkin), [Newgrounds](https://www.newgrounds.com/portal/view/770371), and [GitHub](https://github.com/ninjamuffin99/Funkin).
		+	Seeing as HaxeFlixel was not built for VR, FNFVR is built from the ground up in the [Godot game engine](https://godotengine.org/), using open source plug-ins to manage both PCVR and Quest standalone VR (although the PC version is superior in every way lol)
		+	This is *NOT* a modification of FNF, but it will follow the same licenses as if it were one.
		+	Follow the [FNFVR Twitter](https://twitter.com/FunkinVR) for quick updates!
		+	And join the [FNFVR Discord](discord.gg/fnfvr) to talk about the game with other people!
	+	What's it all about?
		+	*A fresh new take on the FNF formula!* Hit the notes with your hands with a layout reminiscent of games like Guitar Hero and face your opponent head-on... literally!  
		+	*New VR-exclusive mechanics!* Do things you could only dream of pulling off in 2D--like for example, dodging Pico's bullets in Blammed!  
		+	*Robust level creation system!* Easily create new levels of your own with the source, and if you wanna get real fancy, you can also create interruptable asynchronous events (mumbo jumbo for cool mechanics that can be paused or straight up deleted when exiting to the main menu).  
		+	*Adjustable step zone!* Don't like the placement of the lanes in front of you? Then move it yourself, *idiot!*  
		+	*And more now, and more to come!* The team is hard at work creating new stuff and making improvements to the stuff that's already there. In fact, this GitHub is open to bug reports and suggestions just for that purpose! 

1.	**Boxday**
	-.	Source:	https://github.com/MrEliptik/boxday
	-.	Website:	https://mreliptik.itch.io/boxday
	-.	Info:	
	+	Put boxes on the right conveyor belt to get points by matching the label color to the conveyor color. Be careful, there are garbage boxes that you should throw out. 
	+	Boxes will spawn faster and faster infinitely, so stop whenever you want!
	+	Made for the Quest 2 (should work on Quest 1) as a Secret Santa 2021 jam entry. 
	+	Controls
		+	A or X to pause/unpause
		+	Left/Rright triggers to grab and release boxes
		+	Left/Right triggers to select UI
	+	Note
		+	The game is very bare bone but I hope you can still find it funny. 

1.	**Fugitive 3D**
	-.	Source:	https://github.com/FugitiveTheGame/Fugitive3D
	-.	Website:	https://stumpy-dog-studios.itch.io/fugitive-3d
	-.	Info:	A retro multiplayer, objective based, hide and seek game.
	+	https://fugitivethegame.online/
	+	Join our Discord: https://discord.gg/2qk2Spe
	+	The sequel to the 2D game, Fugitive is here! And it's in 333 DDD
	+	Play hide and seek with your friends on a warm summer night. Hide behind bushes as the Cops search for you. Make your way to the end zone without getting caught! If you're friend gets frozen by the police, you have to decide if it's worth trying to go rescue them. Or be the Cops, and drive around in your cop car shinning your flashlight into dark corners.
	+	Features:
		+	Cross-platform! VR and Flat players can play together.
		+	Server browser: Find a game quickly from any platform!
		+	Positional VOIP: hear the fugitives whispering in the bushes as you search for them.
		+	Watch the Replay: At the end of the round talk with everyone about how close they were to catching you as you all watch a replay over the round!
		+	Free and Open Source!
		+	Even runs on Android phones, so your one lame friend with no VR and no PC can still join in on the fun :P

1.	**Escape From The Void**
	-.	Source:	https://github.com/DoubleSept/eftv-demo
	-.	Website:	https://doublesept.itch.io/escape
	-.	Info:	Source only for demo, full game is closed source
	+	Demo version of [Escape From The Void](https://doublesept.itch.io/escape).
	+	Game description
		+	A VR Coop game in which one player, using the headset, has to describe his environment to the other player.
		+	This projects contains example levels (while [eftv-core](https://github.com/DoubleSept/eftv-core) contains the logic)
		+	Made for Godot 3.0

1.	**DeltaPhi - ΔΦ**
	-.	Source:	https://github.com/quendera/deltaphi
	-.	Website:	https://cystyr.itch.io/deltaphi
	-.	Info:	Play with microphone and headphones.
	+	"From the street to the home, domestic space too must not escape our tentacles. So profoundly ingrained, domestic space has been deemed impossible to disembed, where the home as norm has been conflated with home as fact, as an unremarkable given. Stultifying ‘domestic realism’ has no home on our horizon. Let us set sights on augmented homes of shared laboratories, of communal media and technical facilities. The home is ripe for spatial transformation as an integral component in any process of feminist futurity. But this cannot stop at the garden gates. We see too well that reinventions of family structure and domestic life are currently only possible at the cost of either withdrawing from the economic sphere—the way of the commune—or bearing its burdens manyfold—the way of the single parent. The task before us is twofold, and our vision necessarily stereoscopic: we must engineer an economy that liberates reproductive labour and family life, while building models of familiality free from the deadening grind of wage labour. "
	+	-- Laboria Cuboniks

1.	**Blöcks by Kosmos School**
	-.	Source:	https://github.com/kosmosschool/blocks
	-.	Website:	https://kosmosschool.itch.io/blocks
	-.	Info:	Build electrical circuits to master challenges in VR.
	+	Blöcks is a VR puzzle game made for the Oculus Quest. Build electrical circuits with different Blocks to master increasingly difficult challenges. This is a free early alpha release and the game is not in active development.
	+	🍕 Challenges
	+	Each Challenge has objectives that require you to measure a certain current (Ampere) or voltage (Volts). To successfully complete a challenge, you need to build a circuit with the available Blocks and make sure it has the right current and voltage.
	+	🎉 Installation
	+	Blöcks is only compatible with the Oculus Quest. You can download the apk from Itch and install ("sideload") it on your Quest via SideQuest or manually. You can also clone this project and build it yourself in Godot.
	+	Public code but no license
	+	While we're publishing our source code for everyone to see, we don't grant a license (open source or otherwise), which means the source code is under exclusive copyright. Per GitHub Terms of Service, you're still free to view and fork our code. Our intention with publishing our code is primarily educational. We hope that others who are starting to build VR apps might learn or get inspiration to solve a problem they're working on.
	+	If you have any questions, or want permission to use our code differently, please contact us: canolcer@hey.com

1.	**Snap Blocks**
	-.	Source:	https://github.com/kosmosschool/snap-blocks
	-.	Website:	https://kosmosschool.itch.io/snap-blocks
	-.	Info:	Snap Blocks lets you build whatever you desire with colorful blocks.
	+	Snap Blocks lets you build whatever you desire with colorful blocks in VR.
	+	You don’t need to be Picasso to be creative. Snapping blocks together is fun and easy, and the only limit is your imagination.
	+	The game is an early version and not in active development.

1.	**Rhythm Thrower**
	-.	Source:	https://gitlab.com/yxt0531/rhythm-thrower
	-.	Website:	https://yxt0531.itch.io/rhythm-thrower
	-.	Info:	Rhythm dart game for Oculus Quest with hand tracking support.
	+	Follow the rhythm to throw darts, the closer throw to a beat, the higher score gets, the more accurate throw to the target, the higher score gets.

1.	**Pig Poppa**
	-.	Source:	https://github.com/elocnatsirt/pigpoppa
	-.	Website:	https://elocnat.itch.io/pigpoppa
	-.	Info:	A VR game created for Godot Wild Jam #22. Play it on itch.io:
	+	OBJECTIVE
		+	In Pig Poppa your goal is to collect all of the different colored spray paint cans hidden around the level.
		+	Use your spray cans to paint cool graffiti art! Explore the park and eliminate any angry little pigs that get in your way.
	+	CONTROLS
		+	Menu button opens/closes menu (might be bugged: press on both controllers at beginning of game after starting)
		+	Trigger button and pointing controller teleports
			+	Trigger button selects menu item when it's open
		+	Touchpads enable smooth teleportation
		+	Side buttons grab objects in world
			+	Press/Hold the trigger to use items

1.	**Ataito: The Spirit Swapper**
	-.	Source:	https://github.com/Malcolmnixon/Ataito-Game
	-.	Website:	https://malcolmnixon.itch.io/ataito-the-spirit-swapper
	-.	Info:	Global Game Jam 2022 Submission - Ataito: The Spirit Swapper
	+	A spirit walker must use both his forms to collect all the spirit orbs.
	+	Take your time first, and then try to beat your time!

1.	**Deep Space Immersion**
	-.	Source:	https://github.com/pkowal1982/DeepSpaceImmersion
	-.	Website:	https://pkowal1982.itch.io/deep-space-immersion
	-.	Info:	
	+	Game and test project for using webcam on Linux with Godot Engine.
	+	Deep Space Immersion aims at tracking your head without any special gear and making it fast and cheap, so it can run on older hardware. You can try to use color sticker note or ping-pong ball. Notes are easier to attach but tend to change their color when tilted so balls can prove a better alternative.
	+	Choose marker with contrasting color, green and blue will do nicely, assuming you don't have anything that color in the background.
	+	If you do not have color marker you can try black and white one. Print the [provided file](https://github.com/pkowal1982/DeepSpaceImmersion/blob/master/image/markers.svg) and depending on your camera setup choose the one best working. Remember tracking bw marker is more expensive. 
	+	Windows version does not provide head tracking.

1.	**Quest Arena**
	-.	Source:	https://gitlab.com/yxt0531/vr-arena-quest
	-.	Website:	https://yxt0531.itch.io/quest-arena
	-.	Info:	
	+	A voxel style arena shooter for Oculus Quest, bringing back old-time fun to VR. It's simple, just grab a gun and shoot anything that moves. And yes, you can dual wield shotguns too.
	+	Dedicated server program for Quest Arena.
		+	https://gitlab.com/yxt0531/quest-arena-server
	+	A simple graphics card benchmark tool using GLES 3 renderer. A byproduct of Quest Arena.
		+	https://gitlab.com/yxt0531/no.-7-club-benchmark-tool

1.	**Beep Saber**
	-.	Source:	https://github.com/NeoSpark314/BeepSaber
	-.	Info:	A basic implementation of the Beat Saber VR game mechanic in the Godot Game Engine for Oculus Quest (and other VR headsets)
	+	This is a basic implementation of the beat saber game mechanic for VR using the Godot Game Engine and the Godot Oculus Quest Toolkit. The main objective of this project is to show how a VR game can be implemented using the Godot game engine.
	+	The main target platform is the Oculus Quest but it should also work with SteamVR if you add the OpenVR plugin to the addons folder in the godot project.
	+	Originally this game was (and still is) a demo game as part of the Godot Oculus Quest Toolkit. To keep the demo implementation small this stand alone version was forked so that it can be changed and developed independent of the original demo.

1.	**Voxel Works Quest**
	-.	Source:	https://github.com/NeoSpark314/VoxelWorksQuest
	-.	Website:	https://neospark314.itch.io/voxel-works-quest
	-.	Info:	A prototype for Jog-In-Place locomotion on Oculus Quest using the Godot game engine to explore an infinite procedurally generated voxel world.
	+	Mine and craft in 6DoF, but it's real work.
	+	This is the full source code of the prototype Oculus Quest game Voxel Works Quest (https://neospark314.itch.io/voxel-works-quest or https://sidequestvr.com/#/app/431).
	+	As this was intended as a quick prototype for jog in place locomotion the code is not very clean yet and a lot of shortcuts were taken during development. Feel free to dig into the details here but do not expect it to be a good reference on how to build a VR game.
	+	Starting/Developing on Desktop
		+	Voxel Works Quest uses a modified version of the Godot Voxel Module that needs to be compiled together with the godot engine editor. For an easier start in getting to run this game I have included a prebuild version of the editor (windows only) with the correct voxel engine for windows in the releases of this repository. This should allow to open and run the project without the need to compile godot and the module yourself.

---

##Ports
1.	**WOLF3D-Godot**
	-.	Source:	https://github.com/BenMcLean/WOLF3D-Godot
	-.	Info:	Wolfenstein 3-D recreated in Godot Mono for the Oculus Quest
	+	Everything in this repo is still a work in progress: the game is not playable yet.
	+	This project aims to re-create the experience of the classic 1992 first person shooter game Wolfenstein 3-D and other games running on the same engine (Spear of Destiny and Super 3-D Noah's Ark) for virtual reality, ultimately to make these old games playable on the Oculus Quest in true stereoscopic 3D. Also supporting PC VR.
	+	There has already been an admirable effort at recreating Wolfenstein 3-D in VR so anyone who just wants to play the game in VR right now on their PC should check that version out. However, in my view, that version leaves some gaps which this project aims to fill in:
		1.	This is on the Godot-Mono engine, so the entire technology stack is as open source as possible. This remains true despite the fact that almost none of the original Wolfenstein 3-D code is directly involved in this project. It's a port, but it's not a source port: it is a brand new high-level emulator of the game's rules re-interpreted for VR.
		1.	This version is going to load in all the assets from the original 1992 game files at runtime with no intermediary formats. (beyond adding some XML for things normally compiled into the EXE) The shareware is included but unless you obtain the original MS-DOS game files for the other episodes and games then you can't play them. Files from other platforms are unsupported.
		1.	Apart from rendering in HD, this version is going to keep the aesthetics strictly matching the original 1992 MS-DOS PC version to a ridiculously autistic and even slightly creepy degree. This means emulated Adlib / Sound Blaster sound, no dynamic lighting and no high resolution textures. If you don't like the original pixel art by Adrian Carmack and the original Adlib soundtrack by Robert Prince then this is not the version of Wolfenstein 3-D for you.
		1.	This version is going to have extensive mod support, including directly supporting classic mods and user-made map packs from the original game and/or made with existing modding tools from the community. In fact, the whole thing is being constructed from the beginning such that everything (even the full registered WOLF3D) is treated during development as a mod of the shareware version. Mods that require patching actual new code features into WOLF3D.EXE will probably not run, but most mods will probably run.
		1.	The goal is to make this program work on the Oculus Quest. Other platforms, like PC VR, may also be supported, but the Oculus Quest is the main goal.
	+	At this time, I do NOT plan to work on support for Blake Stone, Corridor 7 or Rise of the Triad.

1.	**Deathchase VR**
	-.	Source:	https://github.com/SteveSmith16384/DeathchaseVR
	-.	Website:	https://stephensmith.itch.io/deathchase-vr
	-.	Info:	
	+	If the above game doesn't work, try https://stevesmith16384.bitbucket.io/deathchasevr/DeathchaseVR.html instead.   I don't think Itch properly handles WebXR pages.
	+	Finally, you can experience the adrenaline rush that is Deathchase in VR.  Based on the classic ZX Spectrum game (voted #1 in the last issue of Your Sinclair) you can race through the forest shooting enemy bikers, tanks and helicopters.  This version is quite basic at the moment, but if I get any feedback I'll add more features.
	+	This game is created in WebXR so it should work most headsets, apart from PSVR and Rift (that I know of).  The only controls are pointing your controller to turn left and right, and press the button to accelerate and shoot. 
	+	Comments, compliments and criticisms are always welcome, either here or at stephen.carlylesmith@googlemail.com . :)

---

##Unsure Source

1.	**The Impossible Crypt**
	-.	Website:	https://neospark314.itch.io/the-impossible-crypt
	-.	Info:	
	+	The Impossible Crypt is a game prototype to test the use of Impossible Spaces for VR Dungeon Crawling on the Oculus Quest using only real physical locomotion.
	+	Note that this is a very early prototype. There is no game-play or objective yet and you can only walk around the simple generated dungeon.
	+	The game uses a tile-based generation algorithm to create overlapping dungeon layouts in a limit space. For the algorithm to work properly you need at least 2.5m x 2.5m of free space (better are >= 3.5m x 3.5m). 
	+	The reconfiguration of the space is hidden by a lantern that has a limited illumination radius. This allows to explore a large area by walking only inside a fixed limited space.  It can generate the illusion of actually walking a long distance in a fantasy dungeon. 
	+	The main inspiration for this comes from the 2013 paper Flexible Spaces: https://www.ims.tuwien.ac.at/projects/flexible-spaces and also from the amazing work done by Void Room in Tea for God: https://void-room.itch.io/tea-for-god.

1.	**DestCraft**
	-.	Website:	https://zapina.itch.io/destcraft
	-.	Info:	An Voxel Game like mine craft ..... 
	+	FEATURES - 
		+	Minecraft like Environment
		+	Basic Functionalities
		+	High Requirements
		+	Chunk Generations
		+	Custom Textures
		+	VR support (Even for the cheap ones)
		+	Minecraft like Music and SFX
		+	Available for Windows and Linux.

1.	**While Waiting**
	-.	Website:	https://zattstudio.itch.io/while-waiting
	-.	Info:	Trust the process.
	+	While Waiting is a single-player story and exploration game which utilises one single space to reveal a fascinating story to you, the player. You play as Henry, a young man who revisits his old life to find out things he never wanted to find out. You will help him to find his way through his various mental stages. The story for the game is written by Rebecca Gao. The voices of Dena Darvish Derakhshan and Jennifer Will and others make it a unique adventure for everyone.
	+	Words from the writer:
		+	The making of "While waiting" was a process of creating a puzzle where the task of putting all the pieces back together became the reward in of itself. To tell the tale of a single individual's life through small fragments were both a challenge and a true joy. I, as the writer, hope that you get to know Henry and explore and grow alongside him. Remember - trust the process.
		+	https://zattstudio.com/while-waiting/
		+	https://www.instagram.com/zattworks/
		+	https://www.instagram.com/denadarvish/
		+	https://www.instagram.com/makegao/

1.	**Shagon Daungon**
	-.	Website:	https://pietru.itch.io/shagon-daungon
	-.	Info:	This is Demo/Prototype to see feedback on the project.
	+	Escape the dungon that you have woken inside of. 
	+	Use climbing and jumping to get out from here.
	+	This game requires VR headset to play.
	+	It is not long but I had fun making it so I wish you fun while playing it.

1.	**This. Is. Not. Working.**
	-.	Website:	https://puchik.itch.io/this-is-not-working
	-.	Info:	
	+	A sound-driven VR game created for a sound design class about a student who  is taking a sound design class and trying to finish her project.
	+	Dive into the mind of a student in the last few days before a project deadline.
	+	The focus of this project is the creation of an immersive auditory environment and an interactive and reactive sound system.

1.	**Menace Probe**
	-.	Website:	https://nickofthesouth.itch.io/menace-probe
	-.	Info:	You are tasked with investigating a mysterious device with an unknown origin.

1.	**T3ngist**
	-.	Website:	https://stormplay.itch.io/t3ngist
	-.	Info:
	+	T3ngist is a First Person Shooter game, made to test the mechanics got my other games, just to make sure that they're not awful.
	+	So giving us feedback would be really appreciated!

1.	**Super Generic Shmup (VR)**
	-.	Website:	https://goofyblocks.itch.io/super-generic-shmup
	-.	Info:	
	+	As a test to learn more about vr game development i made a simple space alien shooter. alien portals have started to appear in the city, and only you can save the day...for some reason. it's a little buggy, i haven't gotten motion sick from playing but there is some frame stutter if you kill enemies too fast and shoot excessive bullets.

1.	**Speedroom**
	-.	Website:	https://theklin.itch.io/speedroom
	-.	Info:	Run and Gun!
	+	Grab your guns, shoot all targets, and complete time trials as fast as you can. And then try to do it faster!
	+	The game provides online rankings, you can compare your times and find someone to beat.

1.	**Iso Bowling VR**
	-.	Website:	https://stuarta0.itch.io/iso-bowling-vr
	-.	Info:	
	+	Can’t go out? Throw bowling balls at your neighbours instead!
	+	Knock over all the pins in the least number of throws and you win!
	+	Controls
	+	Developed with HTC Vive.
		+	Room scale VR, slide thumb over trackpad for continuous movement
		+	Press and hold trigger to pick up a bowling ball, swing and release trigger to throw the ball
	+	Why?
	+	Developed during the COVID-19 lockdown for the Tas Jam @ Home game jam with the theme: distance/proximity. Italians had been seen to sing songs on their balconies or even play tennis from rooftop to rooftop. Since I'd rediscovered Wii Sports bowling, I thought I'd combine the two and make VR bowling between Italian apartments :)

1.	**Tiled Land**
	-.	Website:	https://andreterra.itch.io/tiled-land
	-.	Info:	I found some awesome cc assets and put this apk together.

1.	**VR Orb Shooter**
	-.	Website:	https://khrisf999.itch.io/vr-orb-shooter
	-.	Info:	Shoot and slash pink floating orbs.

1.	**Five Nights Among Us:VR**
	-.	Website:	https://teemolert.itch.io/fnauvr
	-.	Info:	
	+	Hey Hey Hey Crewmate, you survived 5 nights on the Skeld once, 
	+	can you do it again in VR?
	+	Please leave a rating of the game once you play it.
	+	If you post a video or stream gameplay please post a link to the game.
	+	Play the original game [here](https://teemolert.itch.io/fnau)
	+	Have fun :) 

1.	**Far Stars Prototype (Godot Engine)**
	-.	Website:	https://ceredev.itch.io/far-stars-prototype-godot-engine
	-.	Info:	This is the same prototype of Far Stars (made in Unity) but in Godot Engine.

1.	**Watch Grass Grow**
	-.	Website:	https://aresiel.itch.io/grass
	-.	Info:	
	+	Imagine watching grass grow IN VIRTUAL REALITY!!! Discord server [here](https://discord.gg/zhyM3Ut).
	+	I lost the files for this, so development canceled! I recommend [this](https://fr0z3nr.itch.io/grass-watching-simulator-2017-vr) instead as it's probably a lot better.
	+	There's also an web version, which is partially work in progress. 
	+	It can be found [here](https://watch-grass-grow.glitch.me/index.html).
	+	Made with [Godot](https://godotengine.org/).

1.	**RoomWithAView**
	-.	Website:	https://ark1ve.itch.io/roomwithaview
	-.	Info:	Room With A View is a VR room builder game.
	+	Recreate your physical room in VR. Place animated posters on the wall, lay on your couch, interact with your computer desktop in the palm of your hand or on a 70 inch screen.
		+	Use elevators to make a floor for digital painting, another for not exercising in, a third for your home cinema! Change your environment from a selection of dynamic places, maybe overlooking a beach boardwalk, or a private forest, or outerspace.
		+	Full desktop interaction is supported; why recreate applications for VR when there's already a giant eco system of infinitely better applications out there. Open Gimp or Krita to use a VR screen as a touch sensitive canvas. Watch your favorite videos with VLC or youtube.
		+	Room With A View aims to be a hub for VR experiences, akin to Steam's VR home, but matching your real world space. Listen to music or audio books and use your desktop. When you put something on a counter, it's your real counter. The couch is your actual couch, and you can customize it's look however you want.
		+	Improve, customize, and express yourself through your surroundings for free, through software.
	+	Completely out of left field Demo Release:
		+	Controls:
			+	Trigger to select menus and buttons
			+	Grip buttons to grab/drop items, and leave fullscreen mode
			+	Menu button above the touchpad to toggle the selection menu
			+	Click the center of the touchpad while pointing at an object to open it's context menu
			+	The touch pad sides can be used while placing walls for more precise placement
			+	Increase/Decrease size of screens in fullscreen mode by tapping up or down on the touchpad.
		+	Known issues:
			+	This is alpha level software and there are still some issues. Expect this list to grow and shrink throughout development.
			+	Desktop Viewer Slow Refresh Speed: I've done a lot of work to speed this up, but there's still some areas of improvement. Best way to speed up the desktop viewer is to set the resolution lower on your monitors. With a Nvidia GTX 1080 I get pretty decent video speed between 720 and 1080p. This also helps with visibility as higher resolutions produce hard to read text in the headset.
