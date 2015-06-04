# How to Include Dependencies in your Plugin

**WARNING This page is now out of date!**

If you are creating an add-on in the zap-extensions project then all you need to do is include 3rd party jars in the top level lib directory and a lib directory immediately underneath your package directory.

The 'standard' build targets will do the rest.

We do aim to document this better soon :/

**Previous content for info:**

This page describes how you should include the jar dependencies in your extension. Dependencies are packed in the plugin jar file. To do so, you have to carry out the following two steps:

## 1. Include the dependencies in the extension
First, you have to create a new **lib** folder in **${src}/org/zaproxy/zap/extension/${extension}/**, where **${src}** is the filesystem path to the src folder of your zap-extensions project, and **${extension}** is the name of your extension. You should put in the new lib folder all the jar dependencies of your plugin. _Note_: this new lib folder is not in classpath in your zap-extensions project. Therefore, you might need to either include its path in classpath or to also copy these jars in the zap-extensions/lib folder of your project.

## 2. Make the specific antcall in build.xml
Second, you have to edit the **build.xml** file of the project and include the following lines:
```
<target name="build-pluginName" description="build the pluginName extension">
     <antcall target="build-extensionAndDeps">
          <param name="extension" value="pluginName"/>
          <param name="type" value="alpha"/>
          <param name="version" value="1"/>
     </antcall>
</target>
```
_pluginName_ and the values of _extension_, _type_ and _version_ have to be changed according to your plugin information. The previous code will call the build-extensionAndDeps target that is defined as follows:
```
<target name="build-extensionAndDeps" description="build the specified extension and include its dependencies">
     <jar jarfile="${dist}/zap-ext-${extension}-${type}-${version}.jar" update="true" compress="false">
          <zipfileset dir="${build}" prefix="">
               <include name="org/zaproxy/zap/extension/${extension}/**" />
          </zipfileset>
          <zipgroupfileset dir="${src}/org/zaproxy/zap/extension/${extension}/lib/" includes="*.jar" />
          <zipfileset dir="${src}" prefix="">
               <include name="org/zaproxy/zap/extension/${extension}/Messages*" />
          </zipfileset>
     </jar>
</target>
```
If your plugin did not have to pack dependencies, you would need to use: ```
 <antcall target="build-extension"> ``` Instead of: ```
<antcall target="build-extensionAndDeps"> ```