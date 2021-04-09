*** Lists and Keys ***    

* Rendering Multiple Components :
You can build collections of elements and include them in JSX using curly braces {}.
-- For example Refer demo-01

* Basic List Component:
Usually you would render lists inside a component.
-- For example Refer demo-02

* Keys:
Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity
The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys
When you don’t have stable IDs for rendered items, you may use the item index as a key as a last resort.We don’t recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.

* Extracting Components with Keys:
Keys only make sense in the context of the surrounding array.
For example, refer demo-03
A good rule of thumb is that elements inside the map() call need keys

* Keys Must Only Be Unique Among Siblings.
Keys used within arrays should be unique among their siblings. 
However they don’t need to be globally unique. We can use the same keys when we produce two different arrays: