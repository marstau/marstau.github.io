---
layout: post
title: JAR creation failed. See details for additional information
category: 编程开发
tags: android java
keywords: 
description: 
---

## ERROR

```
JAR creation failed. See details for additional information. Class files on classpath not found or not accessible for: 'Server Manager/src/me/Zahach/ServerManager/main.java'
```

## Solution


工程设置问题,不要勾选外部编译器自动编译


#### `方法1`

```
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
	<name>projectname</name>
	<comment></comment>
	<projects>
	</projects>
	<buildSpec>
		<buildCommand>
			<name>com.android.ide.eclipse.adt.ResourceManagerBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.android.ide.eclipse.adt.PreCompilerBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>org.eclipse.ui.externaltools.ExternalToolBuilder</name>
			<triggers>full,incremental,</triggers>
			<arguments>
				<dictionary>
					<key>LaunchConfigHandle</key>
					<value>&lt;project&gt;/.externalToolBuilders/org.eclipse.jdt.core.javabuilder.launch</value>
				</dictionary>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.android.ide.eclipse.adt.ApkBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>org.eclipse.ui.externaltools.ExternalToolBuilder</name>
			<triggers>full,incremental,</triggers>
			<arguments>
				<dictionary>
					<key>LaunchConfigHandle</key>
					<value>&lt;project&gt;/.externalToolBuilders/SDK_Builder.launch</value>
				</dictionary>
			</arguments>
		</buildCommand>
	</buildSpec>
	<natures>
		<nature>com.android.ide.eclipse.adt.AndroidNature</nature>
		<nature>org.eclipse.jdt.core.javanature</nature>
	</natures>
</projectDescription>

```

改成

```
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
	<name>projectname</name>
	<comment></comment>
	<projects>
	</projects>
	<buildSpec>
		<buildCommand>
			<name>com.android.ide.eclipse.adt.ResourceManagerBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.android.ide.eclipse.adt.PreCompilerBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>org.eclipse.jdt.core.javabuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.android.ide.eclipse.adt.ApkBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
	</buildSpec>
	<natures>
		<nature>com.android.ide.eclipse.adt.AndroidNature</nature>
		<nature>org.eclipse.jdt.core.javanature</nature>
	</natures>
</projectDescription>

```

#### `方法2`

properties->Builders,仅勾选Android Resource Manager,Android Pre Compiler, Android Package Builder,其余的如ant自动编译,都去掉勾选。

## Reference