The Structure of the Sponge Project
===================================

The Sponge Project consists of different subprojects, hosted in various repositories on Github. Here's a short overview
before going into detail:

+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| Project                                                           | Description                                           | What is done in the repository?                                                 |
+===================================================================+=======================================================+=================================================================================+
| `SpongeAPI <https://github.com/Spongepowered/SpongeAPI>`_         | The API itself                                        | Development of the API itself                                                   |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| `SpongeForge <https://github.com/Spongepowered/SpongeForge>`_     | A SpongeAPI implementation built on top of Forge      | Development of the parts of SpongeForge which rely on Forge                     |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| `SpongeVanilla <https://github.com/Spongepowered/SpongeVanilla>`_ | A SpongeAPI implementation built directly on top      | Development of the Vanilla Counterpart of the SpongeForge repository            |
|                                                                   | of Vanilla Minecraft                                  |                                                                                 |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| `SpongeCommon <https://github.com/Spongepowered/SpongeCommon>`_   | The shared code between SpongeForge and SpongeVanilla | Development of all code which is shared between SpongeForge and SpongeVanilla   |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| `Mixin <https://github.com/Spongepowered/Mixin>`_                 | The tool used to inject the implementations into      | Development of our solution to hook Sponge into the Minecraft server            |
|                                                                   | the underlying code structure                         |                                                                                 |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| `SpongeDocs <https://github.com/Spongepowered/SpongeDocs>`_       | The official SpongeProject Documentation              | Expanding, fixing and writing the SpongeDocs                                    |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
| `Ore <https://github.com/Spongepowered/Ore>`_                     | Our plugin hosting solution                           | Development of our plugin hosting solution                                      |
+-------------------------------------------------------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+




The next image shows the various parts of the Sponge Implementations and how they interact with each other and their dependencies.
On the left side is a typical SpongeForge setup with some SpongeAPI plugins, a Forge mod and a hybrid which uses Forge
(as a mod) and Sponge (as a plugin) to interact. On the right side there's a typical SpongeVanilla setup. You'll notice
that SpongeVanilla doesn't support Forge mods or the hybrid, because SpongeVanilla is missing the Forge functionality:

.. todo: update image as this one is outdated.

.. image:: /images/contributing/SpongeProject-structure.svg
    :alt: Repo Overview
