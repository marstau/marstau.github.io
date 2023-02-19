---
layout: post
title: CocosBuilder
category: 软件工具
tags: software
keywords: CocosBuilder,mac,ios
description: 
---

## **Flatten paths when publishing**[More](https://github.com/cocos2d/CocosBuilder/blob/master/Documentation/2.%20Setting%20up%20a%20New%20Project.md)

If checked, all file paths in the exported ccbi-files will be flattened (e.g. mySubDirectory/myImage.png will be transformed to myImage.png).

So when the resources are added in Xcode, they need to be added as yellow folders. 

If not checked, you should add your resources as blue folders in Xcode.

## zorder

z-order is set implicitly by cocosbuilder.结点的位置决定了z-order的相对深度,越往下,则离观察者越近. 

## Don't assign, Doc root var and Owner var[More](http://stackoverflow.com/questions/15107426/what-is-the-difference-between-doc-root-var-and-owner-var-in-cocosbuilder)

* `Don't assign`: Simply means that you are not using the Code Connections.
* `Doc root var`: means that you are connecting a custom class cocos2d class. This will glue/connect the object in your document (CCB stage/file) to your code. This option is convenient but you must make ensure that root node's controller object is provided.

  Sometimes you need to be able to access member variables from and get callbacks to another object than the root node of a ccb-file. To do this you will need to pass a owner to the CCBReader.
* `Owner var`: provides you with more flexibility by allowing you to connect to a variable other then the root node. You can glue it to any variable of your choosing.

  ```
 // CCBReader.cpp line 627
 Ref*  target = nullptr;
if(memberVarAssignmentType == TargetType::DOCUMENT_ROOT)
{
	target = _animationManager->getRootNode();
} 
else if(memberVarAssignmentType == TargetType::OWNER)
{
	target = this->_owner;
}
  ```

## CCBPProperties.plist format[More](https://github.com/cocos2d/CocosBuilder/blob/master/Documentation/X1.%20Creating%20Node%20Plug-ins.md)

### Required keys


<table>
    <tr>
        <th>Key</th><th>Type</th><th>Comment</th>
    </tr>
    
    <tr>
        <td>className</td><td>String</td><td>The name of the main class when loaded into an app, e.g. CCMyCocosNode.</td>
    </tr>
    
    <tr>
        <td>editorClassName</td><td>String</td><td>The name of the class used by the editor (often the same as className), e.g. CCBPMyCocosNode.</td>
    </tr>
    <tr>
        <td>inheritsFrom</td><td>String</td><td>The name of the class's super class, this is used to display the inspector panels of the super class, e.g. CCSprite.</td>
    </tr>
    <tr>
        <td>canHaveChildren</td><td>Boolean</td><td>Yes, if it should be possible to add children to this node in CocosBuilder.</td>
    </tr>
    
    <tr>
        <td>properties</td><td>Array</td><td>List of PlugInProperty as described below.</td>
    </tr>
    
    
</table>
###  Optional keys

<table>
    <tr>
        <th>Key</th><th>Type</th><th>Comment</th>
    </tr>
    <tr>
        <td>propertiesOverridden</td><td>Array</td><td>The format is the same as for the properties-key, but it replaces a property of a super class.</td>
    </tr>
    <tr>
        <td>spriteFrameDrop</td><td>Dictionary</td><td>Specifies what class of object will be created when a sprite frame is dropped on the node. E.g. CCMenuItemImage for a CCMenu, see SpriteFrameDrop described below for details.</td>
    </tr>
    <tr>
        <td>requireChildClass</td><td>Array</td><td>Array of String:s that defines which classes are allowed as children for this node. E.g. CCMenu only allows CCMenuItemImage as children.</td>
    </tr>
    <tr>
        <td>requireParentClass</td><td>String</td><td>Specifies if this node can only be added as child to a specific type of node. E.g. CCMenuItemImage can only be added to CCMenu.</td>
    </tr>
</table>

### PlugInProperty

A PlugInProperty defines how a property should be displayed in CocosBuilder and how it should be loaded into an app by CCBReader. It is a dictionary with the following keys. Which property type:s are supported and how they are *serialized* (for the default value) is defined in the Property Types document.


* Required keys

  <table>
    <tr>
        <th>Key</th><th>Type</th><th>Comment</th>
    </tr>
    <tr>
        <td>type</td><td>String</td><td>The property type, e.g. Point or Float.</td>
    </tr>
    <tr>
        <td>displayName</td><td>String</td><td>What label should be associated with the type, e.g. Content Size.</td>
    </tr>
    <tr>
        <td>name</td><td>String</td><td>The name of the property to set on the node (not required for type Separator, SeparatorSub and StartStop).</td>
    </tr>
</table>

* Optional keys

  <table>
    <tr>
        <th>Key</th><th>Type</th><th>Comment</th>
    </tr>
    <tr>
        <td>default</td><td>n/a</td><td>Default value, serialized as described in the Property Types document.</td>
    </tr>
    <tr>
        <td>readOnly</td><td>Boolean</td><td>Set to YES if this property should be read only, e.g. YES for contentSize in CCSprite.</td>
    </tr>
    <tr>
        <td>dontSetInEditor</td><td>Boolean</td><td>If set to YES this property will not be set or read from the node by the editor. Instead, the value will be saved in a separate variable. Requires the default value to be specified.</td>
    </tr>
    <tr>
        <td>platform</td><td>String</td><td>Set this key if the property should only be used on a specific platform. Valid values are Mac or iOS.</td>
    </tr>
    <tr>
        <td>affectsProperties</td><td>Array</td><td>Array of String:s that defines which other properties should be updated when this value changes. E.g. when changing the texture of a sprite, it affects its contentSize.</td>
    </tr>
    <tr>
        <td>extra</td><td>String</td><td>Different uses for different type:s, see the Property Types document for details.</td>
    </tr>
</table>

### SpriteFrameDrop

The SpriteFrameDrop structure is used to specify the behavior when a sprite frame is dropped onto a scene from the assets palette.(将project视图下的图片(.png)拖放到timeline中时,此节点自动生成为CCSprite类型)

* Required keys

  <table>
  <tr>
  <th>Key</th><th>Type</th><th>Comment</th>
  </tr>
  
  <tr>
  <td>className</td><td>String</td><td>The name of the class to create, e.g. CCSprite.</td>
  </tr>
    
  <tr>
        <td>property</td><td>String</td><td>The name of the property to assign the dropped sprite frame to, e.g. displayFrame for CCSprite.</td>
  </tr>
  </table>

  ![](/Resources/CocosBuilder_usage_1.png)

## Reference

* <https://github.com/cocos2d/CocosBuilder/blob/master/Documentation/X1.%20Creating%20Node%20Plug-ins.md>

