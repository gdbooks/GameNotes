
```cs
public class GridPartition : SpatialPartition {
    protected class GridElement {
        List<GameObject> objects;
    }
    
    protected GridElement[][] gameGrid;
    protected Dictionary <GameObject, GridElement> objectMap;
    
    public void AddObject(GameObject object) {
        int xPos = object.position.x / gameGrid.Length;
        int yPos = object.position.y / gameGrid[0].Length;
        
        objectMap.Add(object, gameGrid[xPos][yPos]);
        gameGrid[xPos][yPos].objects.Add(object);
    }
    
    public void RemoveObject(GameObject object) {
        if (objectMap.ContainsKey(object)) {
            objectMap[object].objects.Remove(object);
            objectMap.Remove(object);
        }
    }
    
    public void UpdateObject(GameObject object) {
        if (objectMap.ContainsKey(object)) {
            objectMap[object].objects.Remove(object);
            
            int xPos = object.position.x / gameGrid.Length;
            int yPos = object.position.y / gameGrid[0].Length;
            
            gameGrid[xPos][yPos].objects.Add(object);
        }
    }
    
    public GameObject FindObject(string name) {
        foreach(KeyValuePair<GameObject, GridElement> kvp in objectMap) {
            if (kvp.Key.name == name) {
                return kvp.Key;
            }
        }
        return null;
    }
    
    public List<GameObject> GetObjects(Camera camera) {
        AABB cameraAABB = camera.GetAABB();
        cameraAABB.Expand(5, 5, 5);
        return GetObjects(cameraAABB);
    }
    
    public List<GameObject> GetObjects(Sphere sphere) {
    
    }
    
    public List<GameObject> GetObjects(AABB aabb) {
    
    }
}
```