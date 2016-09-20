A scene object is a subclass of game object
A scene can only be created trough Application->CreateScene???

A game object can only be created as a child of the scene or another game object
No public constructor
node->CreateChild("name")
Can re-parent and destroy
Can never parent to null!

Components can only be created by attaching them to game objects
No public constructor
node->AddComponent<T>()
Can not be added to multiple objects
CAn not be re-parented to different object
Can be destroyed

Init order matters! First, init all the game objects on the root node, then it's children, then their children. That is, init by depth!

When a game obeject at a depth is initialized, init all it's components. ORDER MATTERS, it's a list. Should be able to re-order

Because all game objects belong to a scene, maybe make a .scene accessor? Where each game object knows the scene it belong to?

2 component bases Component and SceneComponent
SceneComponents can only be attached to a scene (OCTREE, MANAGER)
They are kind of like singletons
They get inited in add order, but BEFORE all other components