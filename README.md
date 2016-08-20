# Girls First Digital Studio
## Variable - A storage of a value (number, words, etc)
- Think of a variable like an envelope it holds anything you put inside of it.

## Types of Variables - What specific type of values the variable can store.
- Int - Stores integers (whole number negative and positive).
    * public int year = 365;
-  Boolean - Stores true or false values.
    * public bool hired = true;
-  Float - Stores decimal numbers.
    * public float speed = .5f;








# MICROSOFT WORKSHOP

 
## Week 1: May 21 - May 22
- Parents and Youth Orientation 
-  Check-ins and Ice breakers 
-  Introduction to Game Development and Unity 
- Editor tour
	* Basic navigation (e.g. Scene, Game, Directional Light, Console, Project, Asset Store, Inspector),
	* Game objects/Components (e.g. RigidBody, Collider, Transform, Mesh Renderer)
	* Building simple game from 3D primitives
- Created objects Cube, players
- Created a C# Script (CubeMove) for moving the cube in four directions
-  Created Microsoft OneDrive Accounts to save projects












# CubeMove Script:
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

## Week 2: May 28 - May 29
- Introductions to Standard assets (e.g. Materials, Scripts)
- Basic scripting
       * Collision detection for picking up objects
       * Created a game manager
       *  Free building and game designing
- Created new cubes (naming them Danger Zones, Enemies)
      * Stretched them into rectangles (Transform Components)
      * Added color to objects
      * Adding various components to the objects like Rigidbody, Colliders, and collision 
![screen shot 2016-08-06 at 2 43 17 pm](https://cloud.githubusercontent.com/assets/16143142/17632036/6b770298-6094-11e6-8868-421974a87226.png)

- Introduction to Blender
- Created C# Scripts 
      * Enemy-collects objects when the player collides with object
      *Danger Zone- the player dies when it triggers the danger zone (Red Area)

# Enemy Script

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





# DangerZone Script

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



## Week 3: June 4- June 5
- Introduction to the Blender and the Terrain tool
- Used various images from Google Images for game design
- Created objects (ship, Iceberg terrain) and installed them into Unity
- Created landscape and added CubeMove script to ship
- **https://twitter.com/albertolacon/status/739535527339163648**









# THINK RISE NEW YORK WORKSHOP


## Week 1: June 11

- Introduction
- Check-ins 
- Ice breakers
- Introduction to Unity and Blender 
- Presentations of few games by the instructor
- Creating account for Unity 


## Week 2: June 18 
- Check-ins
- Downloading Unity and Blender
- Start to work on first project in unity
- Create two objects( Enemy, Player)
   * Adding Rigidbody 2D (Physics to the object)
   * Adding box Collider 2D (Physics to the object)
- Create C# scripts
   * CubeMove--moves the object player in four directions upon pressing down certain keys
   * Enemy (which was DangerZone in the Microsoft Workshop)
   * WinZone (which was Enemy in the Microsoft Workshop)	 


# CubeMove C# Script

```
using UnityEngine;
using System.Collections;

public class CubeMove : MonoBehaviour {
	  public float speed = .5f;
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






# Enemy C# script

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

#WinZone C# script

```
using UnityEngine;
using System.Collections;

public class WinZone : MonoBehaviour {

    // Use this for initialization
	  void Start () {
	  }
	
	  // Update is called once per frame
	  void Update () {
	  }

	  void OnTriggerEnter(Collider obj){
		    Destroy (obj.gameObject);
		}
}
```


## Week 3: June 25
- Review from last week
- Update CubeMove and Enemy scripts by adding variables speed and lives
- Application.LoadLevel--reloading the game/level
- Learning to use Build Settings
- Learning to use Unity API
- Tagging the cube--“player”
- Adding Canvas and text to game
- Adding color to object/Creating Materials/Assets folder

# Updated CubeMove Script

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

# Lives Script for Enemy Script

```
using UnityEngine;
using System.Collections;

public class CubeMove : MonoBehavior {
	  public float speed = .5f;
	  public static int lives=3;
  	// Use this for initialization 
	  void Start (){
	  }
```

(The 5th line tells it to subtract one from the variable lives when the player collides with the enemy)

```
    void Update () {
	  }
    void OnTriggerEnter(Collider obj){
        Destroy (obj.gameObject);
        Application.LoadLevel("Game");
	  }
}
```
	
(This belongs on the Enemy script and makes it reset the level when you touch (collide) the player object with the enemy object.)

#Week 4: July 2 
- Reviewing CubeMove, Enemy, and WinZone scripts
- Making the text “Game Over!” appear when the lives count reached 0.
- Adding images to objects
- Creating a pick-up system (using the Enemy script) with coins and other collectables
- Understanding how to read the Console and fix errors in code



# Week 5: July 16 
- Rotating the object 45 degrees when it touched the wall
- Using Blender 3D Model Repository to upload 3D Models into Unity
- Parenting the 3D Model to the AI cube into order to place the 3D model on top of the cube
- Using Mesh Renderer to make the cube invisible and make only the 3D model visible
- Creating background using Google Images (e.g. sand and water)
- Creating an object that chases the original object

# AIController Script:
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
# WallController Script:

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

# Week 6: July 23 
- Based on a set of rules: the students completed a game that was required to have:
      * An AI controller object that moved on its own
      * CubeMove, Enemy, WinZone Scripts
      * A rotation once the object touched the wall
      * An object that chased the other object
      * A 3D model parented to the AI Controller
      * An object that the player can control (with the keys--W, A, S, D)
      * Preface to publishing game on Itch.io

---------------------------------------------------------------------

# More Information about C# language:

# Commentaries on Scripts:

# Enemy

![screen shot 2016-08-06 at 3 43 00 pm](https://cloud.githubusercontent.com/assets/16143142/17632118/c2c784dc-6094-11e6-8330-621e1488e901.png)

![screen shot 2016-08-06 at 3 42 39 pm](https://cloud.githubusercontent.com/assets/16143142/17632200/1aaf7074-6095-11e6-8b2a-8c8c7be7b6ae.png)


# CubeMove

![screenshot 78](https://cloud.githubusercontent.com/assets/17395593/17632393/155b4020-6096-11e6-934d-1e29764e3336.png)

