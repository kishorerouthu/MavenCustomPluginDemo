# MavenCustomPluginDemo
This application builds the maven custom plugin which works as follows.

1. This plugin expose the greeting parameter which can be configured in project which uses this plugin.
2. It displays the greeting message on to the console when the configured phase is executed.

@Mojo(name = "sayhi", requiresProject = false, defaultPhase = LifecyclePhase.COMPILE)
public class GreetingMojo extends AbstractMojo {

    @Parameter( property = "greeting", defaultValue = "Hello, world!")
    private String greeting;

    public void execute() throws MojoExecutionException {
        getLog().info(greeting);
    }
}

GreetingMojo class is simple mojo annotated with @Mojo annotation with configuration properties.
@Mojo(name = "sayhi", requiresProject = false, defaultPhase = LifecyclePhase.COMPILE)

- Name specified the goal of the plugin
- requiresProject defines whether the project is required to execute the plugin.
- defaultPhase it is the default phase when this plugin to be executed.

Parameter annotation defines the configuration property that dynamically taken from the user of the plugin
@Parameter( property = "greeting", defaultValue = "Hello, world!")

- property is the name of the parameter
- defaultValue it takes this values nothing is configured

Note : In pom.xml definition packaging should be maven-plugin.
       <packaging>maven-plugin</packaging>
