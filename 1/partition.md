

```cs
interface SpatialPartition {
    public void AddObject(GameObject object);
    public void RemoveObject(GameObject object);
    public void UpdateObject(GameObject object);
    public GameObject FindObject(string name);
    
    public List<GameObject> GetObjects(Camera camera);
    public List<GameObject> GetObjects(Sphere sphere);
    public List<GameObject> GertObjects(AABB aabb);
}
```

```cs
public class GridPartition {
    protected class GridElement {
    
    }
    
    protected Dictionary <GameObject, GridElement> objectMap;
    
    public void AddObject(GameObject object) {
        objectMap.Add(object, 
    }
}
```