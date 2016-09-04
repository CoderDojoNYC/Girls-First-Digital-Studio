# Girls First Digital Studio Curriculum
## Girls First Digital Studio
Girls First Digital Studio is an interactive weekly class that engages and helps girls create their own games and allows them to explore their technological creativity. Our program, GFDS, is free and meets for six weeks, half a day each. We produced this curriculum for girls who would like to attend or who have attended this program.
## What is Unity 3D?
Unity 3D is a free program that allows users to create any 2D or 3D interactive game with characters and objects. Users can use one of a variety programming languages, such as C#, JavaScript, C, C++, Python, and Boo. In Girls First Digital Studio (GFDS), we create games using the language C#.
## What is Blender?
Blender is a free and open sourced 3D modeling software that enables its users to create objects and designs of their own. In GFDS, we create ships using Blender and install them into Unity for our games.

## Introduction to C# 
### Variables
- Def: A storage of a value (number, words, etc)
- Think of a variable like an envelope it holds anything you put inside of it

### Types of Variables 
- Int - Stores integers (whole number negative and positive)
	* public int year = 365;
-  Boolean - Stores true or false values
	* public bool hired = true;
-  Float - Stores decimal numbers
	* public float speed = .5f;

## Game #1: Introduction to Game Development and Unity
- Downloading Unity and Blender
- Editor tour
- Navigation through Unity setup (e.g. Scene, Game, Directional Light, Console, Project, Asset Store, Inspector),
- Learning about Components, which are used to manipulate Game Objects (e.g. RigidBody, Collider, Transform, Mesh Renderer)
  - Adding Rigidbody 2D (Physics to the object)
  - Adding box Collider 2D (Physics to the object)
- Learning to build simple game from 3D primitives
- Learning to create objects (Cube, players)
- Learning to write a C# Script (CubeMove) for moving the cube in four directions by pressing down certain keys
- Creating and using Microsoft OneDrive Accounts to save projects

## CubeMove Script:
```
using UnityEngine;
using System.Collections;
	
public class CubeMove : MonoBehaviour {
	public float speed = .5f;
	
	// Use this for initialization
	void Start () {	
	}
	//Update is called once per frame
	void Update () {

	    if(Input.GetKey(KeyCode.W)){
			    transform.position += new Vector3 (0, 0, speed);
		  }
		  if(Input.GetKey(KeyCode.S)){
			    transform.position += new Vector3 (0, 0, -speed);
		  }
		  if(Input.GetKey(KeyCode.A)){
			    transform.position += new Vector3 (-speed, 0, 0);
		  }
		  if(Input.GetKey(KeyCode.D)){
			    transform.position += new Vector3 (speed, 0, 0);
		  }
	}
}
```

## Development on Basic Game Objects Created
- Learning to use the Game Manager
- Creation of new cubes and learning how to change their properties
  - Stretching them into rectangles (Transform Component)
  - Adding various components to the objects-- Rigidbody, Colliders  
- Introduction to Standard assets (e.g. Materials)
  - We learn to add color and paste pictures onto objects by creating a folder, “Materials” in our Assets folder

![screen shot 2016-09-03 at 1 44 52 pm](https://cloud.githubusercontent.com/assets/21973154/18226670/13350918-71dd-11e6-8760-47571470e0ec.png)

## Introduction to New Objects and Scripts
- Creating C# Scripts (“Danger Zone”, “Enemy”) and attaching them to the new cubes we had created
- “Enemy”- a pickup system. Collects objects when the player collides with object
- “Danger Zone”- the player dies when it triggers the danger zone (Red Area)

## Enemy Script:
```
using UnityEngine;
using System.Collections;
using UnityEngine.UI;

public class Enemy : MonoBehaviour {

      // Use this for initialization
      void Start () {
      }

      // Update is called once per frame
      void Update () {
        }

      void OnTriggerEnter(Collider obj){
            CubeMove.lives -= 1;
            Destroy (obj.gameObject);
            Application.LoadLevel(0);
        }
}
```
## DangerZone Script:
```
using UnityEngine;
using System.Collections;
using UnityEngine.UI;

public class DangerZone : MonoBehaviour {

    // Use this for initialization
    void Start () {
    }

    // Update is called once per frame
    void Update () {
    }

    void OnTriggerEnter(Collider obj){
        if (obj.tag == "player") {
           Destroy (obj.gameObject);
        }
    }
}
```

## Adding Lives and Reloading Level
- Updating CubeMove by adding variables speed and lives. 
	* Setting the “speed” to a certain constant allows us to control how fast the cube will move when we activate the right keys (recall: CubeMove script).
	* We want our game to have a certain lives count so that the game is over when that lives count reaches 0. Otherwise, the game would never end.
	
```
using UnityEngine;
using System.Collections;

public class CubeMove : MonoBehavior {
      public float speed = .5f;
      public static int lives=3;
    // Use this for initialization 
      void Start (){
      }
}
```

- Application.LoadLevel()--reloading the game/level
	* Learning to use Build Settings--which allows us to reload the level
	* Learning to use Unity API--this is a website that allows us to search for functions or other Unity/coding tools in case we forget
	
```
void Update () {
      }
void OnTriggerEnter(Collider obj){
	Destroy (obj.gameObject);
        Application.LoadLevel("Game");
      }
```
(This belongs on the Enemy script and makes it reset the level when you touch (collide) the player object with the enemy object.)

- Adding a Canvas and text to the game (such as “Lives: ” and “Game Over!”
	* Using Mesh Renderer and adding code to Enemy script to enable “Game Over!” to only appear after the lives count reaches 0.

##  Updated CubeMove Script
```
using UnityEngine;
using System.Collections;

public class CubeMove : MonoBehaviour {
      public float speed = .5f;
      public static int lives=3;
      // Use this for initialization
      void Start () {
    }

      // Update is called once per frame
      void Update () {

            if(Input.GetKey(KeyCode.W)){
                  transform.position += new Vector3 (0, 0, speed);
            }
            if(Input.GetKey(KeyCode.S)){
                  transform.position += new Vector3 (0, 0, -speed);
            }
            if(Input.GetKey(KeyCode.A)){
                  transform.position += new Vector3 (-speed, 0, 0);
            }
            if(Input.GetKey(KeyCode.D)){
                  transform.position += new Vector3 (speed, 0, 0);
              }
        }
}
```
(Using the variable Speed it’s able to change the speed of the controls. Lives is also created to keep track of how many lives are in the game at that moment.)

## Updated Enemy Script
```
using UnityEngine;
using System.Collections;
using UnityEngine.UI;

public class Enemy : MonoBehaviour {
    public Text text;
      // Use this for initialization
      void Start () {
      }

      // Update is called once per frame
      void Update () {
            if (CubeMove.lives == 0) {
                  text.enabled = true;
            }
      }
      void OnTriggerEnter(Collider obj){
            CubeMove.lives -= 1;
            Destroy (obj.gameObject);
            Application.LoadLevel(0);
        }
}
```

## Game #2: Introduction to Blender and Blender 3D Repository
- Introduction to Blender, an open-sourced program that allows users to create their own objects
	* Using Blender to create our own ship designs and installing them into Unity
	* Adding CubeMove Script to ship
- Introduction to the Terrain tool in Unity
	* Building a terrain for Blender object in Unity (i.e. ship on a terrain of icebergs)
- Used various images from Google Images for game design
- Here is a model game that shows what we learned:
https://twitter.com/albertolacon/status/739535527339163648

##  A New Game: Using AI Technology
- Writing code (“AI Controller”) for an object (a cube) to be able to move forward by itself (without the help of a pressed down key)
	* Rotating the object 45 degrees when it touched the wall (using creating a Wall Controller code)
- Fixing a 3D image of an animal onto our self-moving object (because cubes don’t move on their own) so that it appears that the only thing moving is the animal
	* Using Blender 3D Model Repository to upload 3D Models into Unity
	* Parenting the 3D Model to the AI cube into order to place the 3D model on top of the cube
	* Using Mesh Renderer to make the cube invisible and make only the 3D model visible
- Creating background using Google Images (e.g. sand and water)
- Creating an object that chases the original object (by writing an AI2 Controller Script)

## AIController Script
```
using UnityEngine;
using System.Collections;

public class AIController : MonoBehaviour {
      public float speed = 2.0f;
        // Use this for initialization
        void Start () {
        }
        // Update is called once per frame
        void Update () {
             transform.Translate (Vector3.forward * Time.deltaTime * speed);
      }
}
```

## AI2Controller Script
```
using UnityEngine;
using System.Collections;

public class AI2Controller : MonoBehaviour {

    //these are comments
    
    //saves the object that you want to follow as a Transform and is called target.  The 'public' allows this to be visible in the unity inspector

    //so that you can drag and drop the object you want to follow in it's property field.

    public Transform target;

    public float speed;

    // Update is called once per frame

    void Update () {

   	 float step = speed * Time.deltaTime;

   	 //sets the position of this object constantly throughout the game runtime.  each refresh sets the direction it moves to be the vector between this object(transform.position) and the

   	 //object to follow (target.position)

   	 transform.position = Vector3.MoveTowards (transform.position, target.position, step);
    }
}
```

## WallController Script
```
using UnityEngine;
using System.Collections;

public class WallController : MonoBehaviour {
      // Use this for initialization
      void Start () {
      }
      // Update is called once per frame
      void Update () {
      }
      void OnTriggerEnter(Collider obj) {
            if (obj.tag == "AI") {
                  transform.Rotate (new Vector3 (0, 180, 0));
                  transform.Rotate (new Vector3 (0, 45, 0));
            }
    }
}
```

## Our Final Project Using AI Controls
- Based on a set of rules: the students completed a game that was required to have:
	* An AI controller object that moved on its own
	* CubeMove, Enemy, WinZone Scripts
	* A rotation once the object touched the wall
	* An object that chased another object
	* A 3D model parented to the AI Controller
	* An object that the player can control (with the keys--W, A, S, D)
	* All of our students published their games on Itch.io
## Some Neat Unity Tricks to Remember
- Tagging the cube--“player” so that we can refer to the gameObject that we want (by calling its name)
- Understanding how to read the Console and fix errors in code


---------------------------------------------------------------------

## More Information about C# language:

### Commentaries on Scripts:

#### Enemy:

```
using UnityEngine;
using System.Collections;
using UnityEngine.UI;
// Make sure to add the above line into your script. This allows you to use the user interface codes like ‘Text’
public class Enemy : MonoBehaviour {
		// this is the property that saves the Text Object as a variable that you can manipulate 
	public Text text;
		// Use this for initialization
	public Text livesText;
		// this is the second object that only handles numbers (the number of lives the player has )
	void Start () {
	
	}
	// Update is called once per frame
	void Update () {
	// this is an if statement that checks if the live variable in another script (which is a static variable ) is less than or equal to zero
  	// if so it makes the first text object visible 
	if (NameOfScript.lives == 0) {
			text.enabled = true;
		}
	}
	// this is constantly setting the second tect object to whatever the current number is for the lives variable inside the other script
	LivesText.text = “ “ + (NameOfScript.lives);
	}
}

```

```
using UnityEngine;
using System.Collections;
using UnityEngine.UI;
// Make sure to add the above line into your script. This allows you to use the user interface codes like ‘Text’
public class Enemy : MonoBehaviour {
		// this is the property that saves the Text Object as a variable that you can manipulate 
	public Text text;
		// Use this for initialization
	public Text livesText;
		// this is the second object that only handles numbers (the number of lives the player has )
	void Start () {
	}
//replace [PLAYERCONTROLLERSCRIPT]  with whatever script controls your character 
	// Update is called once per frame
	void Update () {
	// Makes the text box displaying GameOver visible when the player looses enough lives 
		if ([PLAYERCONTROLLERSCRIPT].lives == 0) {
			text.enabled = true;
		}
		//displays  the current life count to the console
		Debug.Log ([PLAYERCONTROLLERSCRIPT].lives);
		//sets the text box displaying the life count to whatever the life count is according to the script 
	 LivesText.text= “ “ +(CubeMove.lives);
}
         void OnTriggerEnter(Collider obj){
	//removes a life if a player has come in contact with this object
	// obj is a reverence variable to whatever object comes in contact with this object … in the case it is the player 
	// this will also rest the level once triggered
		If (obj.tag == “Player” ) {
		[PLAYERSCRIPTLIVES] .lives -= 1;
		Destroy (obj.gameObject);
		Application.LoadLevel(0);
	}
}

```

#### CubeMove:

```
using UnityEngine;
using System.Collections;

public class CubeMove : MonoBehaviour {
	// CubeMove-This class name must be the same as the file name for the entire script.
	public float speed = .5f;
	public static int lives=3;
	// 0.5f is for the speed of the player (cube) and int lives is for the account of the number of lives.
	// Use this for initialization
	void Start () {
	
	// Update is called once per frame
	void Update () {

		if(Input.GetKey(KeyCode.W)){
			transform.position += new Vector3 (0, 0, speed);
		}
		if(Input.GetKey(KeyCode.S)){
			transform.position += new Vector3 (0, 0, -speed);
		}
		if(Input.GetKey(KeyCode.A)){
			transform.position += new Vector3 (-speed, 0, 0);
		}
		if(Input.GetKey(KeyCode.D)){
			transform.position += new Vector3 (speed, 0, 0);
		}
	}
}

```
