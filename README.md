# LearningFPrime F' project

This project was auto-generated by the F' utility tool. 

F´ (F Prime) is a component-driven framework that enables rapid development and deployment of spaceflight and other embedded software applications.
**Please Visit the F´ Website:** https://nasa.github.io/fprime/.

I am using this project as a way to learn the FPrime system and topology on a deeper level, in order to contribute to SRL's avionics team. 

Following JPL's tutorials, I will learn how to create Components, learn how they interact and get more familiar with the groundstation architecture as well.

### Creating a Component

In the first tutorial, the HelloWorld Component is created. 

1. First the files are created through the `fprime-util new --component` command in the command line. 

2. We can add events and commands by editing the `.fpp` script.

3. The `.cpp` and `.hpp` files can be automatically changed by using the `fprime-util impl` command. (Make sure that you save the `.fpp` file before this)

    - Use commands `mv HelloWorld.template.hpp HelloWorld.hpp` and `mv HelloWorld.template.cpp HelloWorld.cpp` to overwrite the previous c++ files.

4. Certain specific details are added to both `.hpp` and `.cpp` files which are implementation-specific.

### Creating a Deployment

A deployment is the actual executable within which all the components run. To create it:

1. Run command `fprime-util new --deployment` and input the desired parameters

2. Add the components that you want. This is done by adding the component to the topology in `<nameOfDeployment>/Top/topology.fpp`, which instantiates and links together the components in the system.
    - Most of the time, those connections are made automatically
    - Done by adding to the list with `instance <nameOfInstance>`

    - We also have to add the instance to the deployment, by creating a statement inside `<deploymentName>/Top/instances.fpp`

3. New telemetry channel should be added to telemetry packet specification. Basically we have to say that we have a new channel of data coming through to gds. This will involve the file `<deploymentName>/Top/<deploymentName>DeploymentPackets.xml`

4. Ensure that everything builds, by running `fprime-util build -j4` inside of the `<projectName>/<deploymentName>Deployment` directory

### Running with `fprime-gds`