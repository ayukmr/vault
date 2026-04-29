# programming log

## 4/13

* roboticsteam4904 -> frc4904
* 2026-code -> 2026
* removed org.usfirst.frc4904
* standard -> lib

## 4/4

* broke shoot + climb into two paths
* added command to outtake fuel through intake

## 4/3

* random tuning, etc.

## 4/2

* the worst practice match ever bc of the pigeon dying
* electronics hopefully fixed pigeon using thicker wires??

todo
* vision offset jank

## 4/1

* fixed intake wobble
* shooter leds!!
* vision websocket stuff
* added brick mode

## 3/30

* added vision + robot stuff for using two cameras

## 3/29

* got single dip auton working

## 3/27

* continued work on autons?

## 3/26

* fixed some stuff (intake encoder and climb auton)?

## 3/25

* tried to get preferences working (unsuccessful)

## 3/23

* started getting new intake working
* figured out problem with prefs
    * immediately setting a key wipes all data
* added leds

todo
* test custom storage
* test climb auton

## 3/22

* (fab) made shooter a bit more horizontal
* verified shooting at different distances
* made climber faster

## 3/20

* fixed pigeon imu
    * added rotation constant to fix drift
* reflashed rio firmware

## 3/16

* set up advantagekit logging
* some other misc stuff surely

## 3/15

* creativity award!!

todo
* something with the pigeon

## 3/14

* fixed climb auton
    * requirements caused sequential group to cancel itself
* tuned shooter to new angle
* optimized hopper roller speeds

## 3/13

* general testing and tuning in practice matches

## 3/11

* driver training and further tuning

## 3/10

* got climb auton path working

## 3/9

* actually tuned shoot from distance
* got absolute pathplanner auton working
    * pigeon drift??
* tuned climber pid

## 3/8

* fixing pose estimator for real
* debugging overheating stuff
* turn towards hub
* allegedly shoot from distance (not really)

## 3/6

* i don’t remember but there were some todos

todo
* shooter vision
* climber pid
* auton

## 3/5

* got intake pid working
* set up vision service on pi

## 3/4

* added bindings for a ps4 controller
* got indexer working and did some testing
* got shooter pid working
    * swapped from motor-based pid to normal wpilib pid

todo
* intake extend/retract pid

## 3/2

* some vision service stuff
* started testing shooter

todo
* shooter pid

## 2/26

* set up the emergency pigeon!!

## 2/25

* added operator bindings for intake and shooter
* more misc navx debugging

## 2/14

* got pathplanner auton working correctly!!
* also added some stuff to elastic for better debugging

todo
* fix robot position from tags
* figure out the initial vision slowdown

## 2/13

* got pathplanner relative -> field positions somewhat working
    * basically .plus was doing more than just adding x and y, so replaced it with that

todo
* the starting position doesn't update properly when running it twice

## 2/11

* made vision faster (~55fps -> ~75fps)
* postponed pose estimator

## 2/9

* taught rookies vision (mostly cv)
* maybe some pose estimator stuff?

todo
* pose estimator

## 2/8

* worked on auton

todo
* 90deg rotations are more like 70deg

## 2/6

* field diagram shown on elastic
* got pose estimator working with vision

## 2/5

* got elastic notifications working! (very important)

## 2/4

* rookies worked on finishing angles in intake subsystem
* continued work on pose estimator, pos/angle work

todo
* run intake subsystem on swerve
* finish vision integration with pose estimator

## 2/2

* tried to get motor-based pid working (unsuccessful)
* updated motor-pidf/pose-estimator and some constants

todo
* probably going to use pose estimator w/ old system?

## 1/29

* tried fixes from james tsudica, inventor of navx
    * basically it doesn’t respect the id choice and is always 0
* worked on getting corpsaline and mayhem bot running
    * some code changes for corpsaline to support xbox and fix swerve

todo
* sparkmaxes started dying??
* get fab to fix swerve whining
    * one of the (mayhem?) bot modules has _really_ stiff rotation

## 1/27

* rookies worked on intake (mostly done)
* random navx debugging (literally nothing worked)
    * found navx3 packaging and also the navx2 somehow
