
```
const changeClass = (tree, oldClass, newClass) => {
	const newTree = _.cloneDeep(tree);
	if (_.has(newTree, 'className')) {
		const newClassName = oldClass === newTree.className ? newClass : newTree.className;
		newTree.className = newClassName;
		return newTree;
	}

	if (newTree.type === 'tag-internal') {
    newTree.children = tree.children.map((node) => changeClass(node, oldClass, newClass));
	 }
	 return newTree;
};

export default changeClass;
```

```
const result = changeClass(tree, 'old-class', 'new-class');
// Результат:
// {
//   name: 'div',
//   type: 'tag-internal',
//   className: 'hexlet-community',
//   children: [
//     {
//       name: 'div',
//       type: 'tag-internal',
//       className: 'new-class',
//       children: [],
//     },
//     {
//       name: 'div',
//       type: 'tag-internal',
//       className: 'new-class',
//       children: [],
//     },
//   ],
// }
```

## Analog
```
const changeClass = (tree, classNameFrom, classNameTo) => {
	const innerFunc = (node) => {
	
	const updatedNode = { ...node };

		if (_.has(node, 'className')) {
			const newClassName = classNameFrom === node.className ? classNameTo :   node.className;
		updatedNode.className = newClassName;
		}

		if (node.type === 'tag-internal') { 
		    const newChildren = node.children.map(innerFunc); 
		    updatedNode.children = newChildren; 
		}
		return updatedNode;
	};
	return innerFunc(tree);
};

export default changeClass;
```