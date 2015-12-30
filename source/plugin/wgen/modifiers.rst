Working with WorldGenerationModifiers
=====================================

For a brief overview of the World Generation process in Sponge, please read :doc:`index`.
Now, let's show how you can begin making your mark on world generation.
All plugins wishing to make changes to a worlds generator must register a ``WorldGeneratorModifier``.
These modifiers are registered globally with a unique id, which may be added to the config of a world
by a server admin to

Creating a WorldGeneratorModifer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Let's start with the format of a ``WorldGeneratorModifier``. First, you need a class which implements
the WorldGeneratorModifier interface:

.. code-block:: java

    import org.spongepowered.api.data.DataContainer;
    import org.spongepowered.api.world.WorldCreationSettings;
    import org.spongepowered.api.world.gen.WorldGenerator;
    import org.spongepowered.api.world.gen.WorldGeneratorModifier;

    public class MyModifier implements WorldGeneratorModifier {

        @Override
        public String getId() {
            return "myplugin:mymodifier";
        }

        @Override
        public String getName() {
            return "MyAwesomeModifier";
        }

        @Override
        public void modifyWorldGenerator(WorldCreationSettings world, DataContainer settings, WorldGenerator worldGenerator) {
            //Make changes here
        }
    }

As you can see, ``WorldGeneratorModifier`` has three methods which we override. The first method is ``getId()``,
which must be overridden to return a constant and unique identifier for your ``WorldGeneratorModifier``.
This value will be used to refer to your ``WorldGeneratorModifier`` from the world configuration.

The second one returns a name, which is a more human-readable form of identification. It does not need to be unique but
nonetheless should be descriptive.

The third overridden method is where you make your changes to the world generator. This method is called by
the implementation when it is creating the world generator for a world which has specified that your
``WorldGeneratorModifier`` should be applied.

The ``WorldGenerationSettings`` and a ``DataContainer`` of additional properties for the world are passed to this method
in order to give context for your changes. For instance, you can use the ``WorldCreationSettings`` to only apply your
generator changes to nether worlds.


Registering a WorldGeneratorModifer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Now that you have created our modifier, you need to register it. A good place to do this is in an
``GamePreInitializationEvent`` {Citation needed}. To register it, simply call ``GameRegistry.registerWorldGeneratorModifier``.

.. code-block:: java

    import org.spongepowered.api.GameRegistry;
    import org.spongepowered.api.event.Listener;
    import org.spongepowered.api.event.game.state.GamePreInitializationEvent;
    import com.google.inject.Inject;

    @Inject GameRegistry registry;

    @Listener
    public void initialize(GamePreInitializationEvent event) {
        registry.registerWorldGeneratorModifier(new MyModifier());
    }

[TODO something about how to specify to use the modifier in the world configuration.]

In the next articles we will look deeper at the changes we can make from our ``WorldGeneratorModifer``.
