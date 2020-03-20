# NeoFPS_OotiiMotionController
Scripts and assets created to integrate NeoFPS and the Third Person Motion Controller by Ootii in order to create NPCs.

## Requirements
This repository was created using Unity 2018.4

It requires the assets [NeoFPS](https://assetstore.unity.com/packages/templates/systems/neofps-150179?aid=1011l58Ft) and [Ootii's Third Person Motion Controller](https://assetstore.unity.com/packages/templates/systems/third-person-motion-controller-15672?aid=1011l58Ft).

## Installation
This integration example is intended to be dropped in to a fresh project along with NeoFPS and Behavior Designer.

1. Import NeoFPS and apply the required Unity settings using the NeoFPS Settings Wizard. You can find more information about this process [here](https://docs.neofps.com/manual/neofps-installation.html).

2. Import Ootii's Third Person Motion Controller asset.

3. Clone this repository to a folder inside the project Assets folder such as "NeoFPS_OotiiMotionController".
	
## Integration

This project is intended as a means to add NPC characters to your NeoFPS projects. It is not intended to add support for switching between first and third person player characters.

Alone this integration will not do anything. The motion controller is used to manage animations and motions for NPCs. Your NPCs will need some form of AI as well. See below.

The integration comes with a demo scene. See `NeoFPS_OotiiMotionController/Demo Scene`.

### Setting up the Player

To setup your player you will need to add a Motion Controller `Actor Core` component.
This component has a `Neo FPS Damage Reactor` applied. This reactor converts damage messages from Motion Controller combatants into damage for your player.

The fastest way to setup the Neo FPS player is to use the `NeoFPS_MotionController_TestSetup` prefab that comes in this integration. This is a modified version of the TestSetup that comes
with Neo FPS. The only real difference is that it uses the `MotionControllerDemoSoloCharacter` prefab which is already setup with the Actor Core component.

### Setting Up NPCs

In order to use the Motion Controller for your on NPCS you will need to do the following:

  1. Configure your NPC to use Motion Controller as you would normally (`Window -> ootii Tools -> Character Wizard` works well, be sure to select the NPC option)
  2. Add a Neo FPS Health Manager, such as `Basic Health Manager`
  3. Add a Neo FPS Damage Handler, such as `Basic Damage Handler`
  4. Add a Neo FPS Surface, such as `Simple Surface`
  5. Add an AI to control the NPC, such as the NEo FPS [Behavior Designer Integration](https://github.com/YondernautsGames/NeoFPS_BehaviorDesigner) (see below for a description of the super simple AI used in the demo)

## AI

NPCs typically need some form of AI. There is a very basic "AI" system included with this integration, however, it is not in any way a real AI system. Maybe it will grow up one
day but for now it's only real purpose is to enable an out of the box demo for Neo FPS and Motion Controller integration. If you are strapped for cash and want to enhance the
AI in this integration please do submit partches to improve the system here. Otherwise you might want to look at the [Behavior Designer Integration](https://github.com/YondernautsGames/NeoFPS_BehaviorDesigner).

### Using the AI

The system consists of `AIBehaviourController` components and `AIBehaviour` scriptable objects. The controllers will process an ordered list of behaviours each `tick` (the frequency of the `tick` is defined)
in the component settings. Each behaviour that can be executed will be executed. You can have multiple AIBehaviourControllers attached to a single NPC. Each controller having a different set of behaviours.

There are a very limited set of behaviours at this time. As noted above the goal of this system is not to be a true AI system, but rather provide enough of an AI system to enable a self contained demo for
this integration. 

Here are some of the behaviours currently included:

  1. NavMeshWander - have a NavMesh agent wander semi-randomly
  2. NavMeshGoTo - go to a specific place on the navmesh
  3. MotionControllerIsAlive - check that a Neo FPS NPC is alive and, if not, play the Death motion in Motion Controller

  ## Open Game Art

  This integration includes some Game Art from http://opengameart.org. These assets are under a CC0 license unless otherwsie stated. You are free to use them without restrictions. Please support
  Open Game Art and the artists who publish there.