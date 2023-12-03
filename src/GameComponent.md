# GameComponent
Each component type should inherit from the base class `GameComponent`.
## Attributes
The component class is mainly implemented so that it's possible to store different types of components in the same container. A virtual class has no attribute, but each compoennt inheriting from GameComponent should define a GameObject member which we will often call `attachedObj`. 
Components should have the two constructor, one with no parameter and empty body and the other one has a parameter which is a reference to the GameObject we want the component to be attached to.
## Virtual methods
|Signature|Description|
|---|---|
static std::string GetType()     | Returns the component type as a string
virtual void Start()             | Called when scene is loaded
virtual void Update()            | Called each frame
virtual void SetGameObject()     | Sets the attached object reference
virtual void* GetGameObject()    | Gets the attached object reference
virtual void ~GameCompoent()     | Destructor, many cleanups like GPU allocations
# Inheritance
+ [GuiObject](GuiObject.html)
+ [Serialized](Serialized.html)
## Destruction
Usually creating temporary objects, manipulating them and then copying them into GameObject components list is not a good idea, and that is due to the cleanup process since there temporary objects will delete either objects to the heap, or GPU allocated objects. Often you would want to add empty obejct to a GameObejct with `AddComponent<T>()` and then do different manipulation on it.
## Getter and Setter
Both methods `GetGameObject()` and `SetGameObject()`  deal with `void*` instead of `GameObject` and that's because of circular dependency: GameObject class uses GameComponent and vice versa.
Those methods are implemented for internal seek, you can use them (in case the component type is casted to GameComponent) but often the component type is known and you would just access it's attached object reference directly. However it's generally unsafe to change the value of the latter.
## Implemented components list
+ [Transform](Transform.html)
+ [Sprite](Sprite.html)
+ [ParticleSystem](ParticleSystem.html)
+ [Collider](Collider.html)
+ [Camera](Camera.html)
+ [TextHandler](TextHandler.html)
+ [Animator](Animator.html)
+ [AudioListener](AudioListener.html)
+ [AudioEmitter](AudioEmitter.html)
+ [Animator](Animator.html)