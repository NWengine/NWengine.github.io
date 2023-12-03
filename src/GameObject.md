//Todo::Copy contructor
# GameObject
GameObject is how "Entity" of "ECS" is called in NWengine. It contains a hashmap of components references with the component's types as keys; you can't have more than one component of the same type. 
## Attributes
|Type 	     | Attribute |Description|
|----------  |---------- |-----------|
|std::string | name      | identifier; read only  |
|std::map<std::string, GameComponent*>  | components| A map of heap allocated components withn their type as key|


## Methods

|Signature|Description|
|---|---|
|void Rename()|Renames the gameobject given the name passed in argument|
|void AddComponent(std::string typename)| Adds component of type "typename"|
|void AddComponent<T>()|Adds component of type T|
|void GetComponent<T>()|Same as addition|
|void GetComponent(std::string typename)|Same as addition|
|void DeleteComponent(std::string typename)|Deletes componenent of type "typename"|

## Inheritance
+ [Serialized](Serialized.html)
## Naming
Gameobjects are identified by their name for now, which means every name is unique. The **name** attribute, for safety, shouldn't be changed manually; hence, you should use the follwing method.<br><br>

- `Rename(std::string newName)` <br><br>

Name will be set to **newName** only when it isn't token, otherwise it will be named **newName** followed by n-th instance of it. For example, if you have in the scene "name", "name0", and "name1", renaming an object "name" will result in "name2".

## Components management
Components can be added to a gameobject using following gameobject's methods:<br><br>
- `AddComponent<T>()` *where T is the typename of the added component.*<br>
- `AddComponent(std::string typename)` *where typename is a string containing the type of the added component.*<br><br>


In order to delete a component, the following method is used:<br><br>


- `DeleteComponent(std::string typename)` <br><br>

In order to get a component, as **AddComponent** methods, you can do so using either component string name or the typename:<br><br>

- `GetComponent<T>()`
- `GetComponent(std::string)`
<br><br>

Components are created in the heap and gameobjects are the main containers of them. However, on the contrary of [Scenes](Scene.html), components aren't deleted in the destructor of gameobject. It's a decision taken in order to allow object copying gameobjects without reallocating space for components.
Freeing manually a GameObject does not free its components, hence you would leak memory (if you don't copy the object into another one). Since most objects are in **sceneObjs** list attribute, the scene abstracts object deletion, you should not have any memory problem if you stick to the abstraction.