# Toy-Robot-Simulator
Operating Instructions
You have two options to send commands to the robot.
The first option is to type in commands in command prompt.
The second option is to provide a file with commands.

To operate the robot by typing commands, start the app from the command prompt with no arguments provided and begin type in commands:

$ npm start
Welcome!
Tell the Robot your first command. Begin by placing the Robot on the playground - PLACE X, Y, F. 'q' to exit.
> PLACE 1 1 SOUTH
> REPORT
> Robot's position is: 1, 1, SOUTH
To operate the robot using a file, create a file with commands, e.g. commands.txt, with the following contents:

PLACE 0,0,NORTH
MOVE
REPORT
LEFT
MOVE
REPORT
Then run the application providing it the file as the first argument:

$ npm start commands.txt
Welcome!
Tell the Robot your first command. Begin by placing the Robot on the playground - PLACE X, Y, F. 'q' to exit.
> PLACE 0,0,NORTH
> MOVE
> REPORT
Robot's position is: 0, 1, NORTH
> LEFT
> MOVE
Warning! You cannot move the robot that way, it can fall.
> REPORT
Robot's position is: 0, 1, WEST
Bellow is a full explanation on how to operate the robot.

The Robot can read in commands of the following form (case insensitive):

PLACE X,Y,F or PLACE X Y F (spaces are acceptable instead of commas)
MOVE
LEFT
RIGHT
REPORT
PLACE X Y F will put the toy robot on the table in position X,Y and facing NORTH, SOUTH, EAST or WEST.

The origin (0,0) can be considered to be the SOUTH WEST most corner.

The first valid command to the robot is a PLACE command, afer that, any sequence of commands may be issued, in any order, including another PLACE command. The application should discard all commands in the sequence until a valid PLACE command has been executed.

MOVE will move the toy robot one unit forward in the direction it is currently facing.

LEFT and RIGHT will rotate the robot 90 degrees in the specified direction without changing the position of the robot.

REPORT will announce the X,Y and F of the robot. This can be in any form, but standard output is sufficient.

A robot that is not on the table can choose the ignore the MOVE, LEFT, RIGHT and REPORT commands.

Input can be from a file, or from standard input.

Constraints
The toy robot must not fall off the table during movement. This also includes the initial placement of the toy robot.

Any move that would cause the robot to fall must be ignored.

Testing Instructions
jasmine-npm is used for testing.
All application components have specs and are tested. You can see their specs here https://github.com/wzup/toy-robot-simulator/tree/master/spec

Run npm test to run all the tests. Or specify the name of the spec against which to run tests:

$ npm test // test all components. runs all possible specs
$ npm test spec/robotSpec.js // test robot functionality only, runs robotSpec
$ npm test spec/messengerSpec.js // test messenger functionality only, runs messengerSpec
$ npm test spec/playgroundSpec.js // test playground functionality only, runs playgroundSpec
Plumbing
The application consists of 5 (five) components:

Robot
Messenger
Playground
RobotFactory
TheToyRobotApp
Robot is a class that represents a robot and defines its functionality. I has five public methods to control the robot:
