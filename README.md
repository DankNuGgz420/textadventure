using UnityEngine;
using UnityEngine.UI;
using System.Collections;

public class TextController : MonoBehaviour {

	public Text text;
	private enum States {cell, mirror, sheets_0, lock_0, cell_mirror, sheets_1, lock_1, freedom};
	private States myState;

	// Use this for initialization
	void Start () {
		myState = States.cell;
	
	}
	
	// Update is called once per frame
	void Update () {
		print (myState);
		if (myState == States.cell)					{State_Cell();
		}else if (myState == States.sheets_0)		{State_sheets_0();
		}else if (myState == States.sheets_1)		{State_sheets_1();
		}else if (myState == States.lock_0)			{State_lock_0();
		}else if (myState == States.lock_1)			{State_lock_1();
		}else if (myState == States.mirror)			{State_mirror();
		}else if (myState == States.cell_mirror) 	{State_cell_mirror();
		}else if (myState == States.freedom)		{State_freedom();
		}
	
		if (Input.GetKeyDown(KeyCode.Space)){
			text.text = "After waking up from a horrible night of booming thunder " +
						"and heavy rain, you find yourself in a dimly lit prison cell. " +
						"Inside your cell are some dirty sheets, a mirror on the wall, and a locked door.\n\n" +
						"Press S to View Sheets, M to view Mirror and L to View Lock";
		}
	}
		
	void State_Cell (){
		text.text = "After waking up from a horrible night of booming thunder " +
					"and heavy rain, you find yourself in a dimly lit prison cell. " +
					"Inside your cell are some dirty sheets, a mirror on the wall, and a locked door.\n\n" +
					"Press S to View Sheets, M to view Mirror and L to View Lock";
		if (Input.GetKeyDown(KeyCode.S))	{myState = States.sheets_0;}
		if (Input.GetKeyDown(KeyCode.L))	{myState = States.lock_0;}
		if (Input.GetKeyDown(KeyCode.M))	{myState = States.mirror;}	
	}
	
	void State_cell_mirror (){
		text.text = " Mirror in hand your ready to get out of this hell. \n " +
					"A foul odor is starting to give away from the sheets, it is still pouring \n " +
					"outside, the lightning reveals the cell door once again.\n\n" +
					"Press S to View sheets \n"+
					"Press L to View lock ";
		if (Input.GetKeyDown (KeyCode.S))	{myState = States.sheets_1;}
		else if (Input.GetKeyDown (KeyCode.L))	{myState = States.lock_1;}
	}
	
	void State_sheets_0 (){
		text.text = "Wow who on earth would sleep with these sheets? " +
					"They are absolutely filthy! " +
					"You can barely stand to hold them.\n\n" +
					"Press R to return to roaming your cell";
		if (Input.GetKeyDown(KeyCode.R))	{myState = States.cell;}
		}
		
	void State_sheets_1 (){
		text.text = "Having a mirror doesn't change the fact those sheets are disgusting. \n\n" +
					"Press R to return to roaming your cell";
		if (Input.GetKeyDown (KeyCode.R))	{myState = States.cell_mirror;}
	}
	
	void State_lock_0 (){
		text.text = " Damn. The lock is strong, theres no way you could break this.\n " +
					"Beyond the door is very fuzzy and dark. The lightning is the only source of light in here.\n " +
					"Nothing interesting here, best move on.\n\n " +
					"Press R to return to roaming your cell";
			if (Input.GetKeyDown (KeyCode.R))	{myState = States.cell;}
		}
		
	void State_lock_1 (){
		text.text = "With shaky hands you hold the mirror through the bars of the cell. \n"+
					"Using the light coming from the cellar window, you can see the reflection from \n"+
					"behind the lock.\n" + 
					"You find see 2 wedge like latches. \n"+
					"You squeeze the rusted latches! \n\n" +
					"Press O to open the door \n" +
					"Press R to return to roaming your cell";
		if (Input.GetKeyDown (KeyCode.O))	{myState = States.freedom;}
		else if (Input.GetKeyDown (KeyCode.R))	{myState = States.cell_mirror;}
	}
		
	void State_mirror (){
		text.text = " Nothing else in the cell is looking this good. \n " +
					"Doesn't seem like this tiny mirror is hard to pry off the wall. \n " +
					"I could take this mirror. hmmm. \n\n " +
					"Press T to take mirror \n" +
					" Press R to return to roaming your cell";
		if (Input.GetKeyDown (KeyCode.T))	{myState = States.cell_mirror;}
		else if (Input.GetKeyDown (KeyCode.R))	{myState = States.cell;}
	}
	
	void State_freedom (){
	text.text = "You blindly run as fast as you can down the dark humid corridor! \n" +
				"Looks like theres 2 paths left and right. \n" +
				"Both left and right paths look terrifying, both lifeless and grim. \n" +
				"Which way will you take? \n\n" +
				"Press Left arrow for Left \n"+
				"Press Right arrow for Right\n";
	if (Input.GetKeyDown (KeyCode.RightArrow))		{myState = States.cell;}
	else if (Input.GetKeyDown (KeyCode.LeftArrow))	{}
	//Ignore this else if (myState == States.freedom)				{myState = States.cell;}
	}
	
	
	
	
}
