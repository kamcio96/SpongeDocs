======================
The Pagination Service
======================

.. tip::

	For a basic understanding of services, make sure you read :doc:`../services` first.

The ``PaginationService`` acts as a way to split up content into discrete pages.
The service provides a ``PaginationBuilder`` with which you can specify attributes such as title, contents, header,
and padding.

Working With the PaginationBuilder
==================================

First obtain an instance of the ``PaginationService``, and create a new ``PaginationBuilder``:

.. code-block:: java

	import org.spongepowered.api.service.pagination.PaginationBuilder;
	import org.spongepowered.api.service.pagination.PaginationService;

	PaginationService paginationService = plugin.getGame().getServiceManager().provide(PaginationService.class).get();
	PaginationBuilder builder = paginationService.builder();

There are two different ways to specify the contents of paginated list:

* With an ``Iterable<Text>``

 .. code-block:: java

	import org.spongepowered.api.text.Text;

	import java.util.ArrayList;
	import java.util.List;

	List<Text> contents = new ArrayList<>();
	contents.add(Text.of("Item 1"));
	contents.add(Text.of("Item 2"));
	contents.add(Text.of("Item 3"));

	builder.contents(contents);

 .. note::

	If the ``Iterable`` is a ``List``, then bidirectional navigation is supported. Otherwise, only forwards navigation
	is supported.

* With an array of ``Text``\ s

 .. code-block:: java

	builder.contents(Text.of("Item 1"), Text.of("Item 2"), Text.of("Item 3"));

You can also specify various other components of a paginated list, such as a title, header, footer, and padding. The
diagram below shows which component is displayed in each part of the paginated list. In the following diagram, the
padding string is shown as the letter `p`.

::

	pppppppppppppppppppppppp Title pppppppppppppppppppppppp
	Header
	Item 1
	Item 2
	Item 3
	...
	ppppppppppppppppppppppp < 2/3 > ppppppppppppppppppppppp
	Footer

To achieve the preceding output, we might use the following builder pattern:

.. code-block:: java

	builder.title(Text.of("Title"))
		.contents(Text.of("Item 1"), Text.of("Item 2"), Text.of("Item 3"))
		.header(Text.of("Header"))
		.footer(Text.of("Footer"))
		.paddingString("p");

.. note::

	With the exception of contents, all components of the paginated list are optional. However, a title is strongly
	recommended

Finally, to send the paginated list to a ``CommandSource``, use ``PaginationBuilder#sendTo(CommandSource source)``.

And thats it! To recap, a fully functional paginated list could be generated and sent to a previously defined
``cmdSource`` using the following code:

.. code-block:: java

	PaginationService paginationService = event.getGame()
		.getServiceManager().provide(PaginationService.class).get();

	paginationService.builder()
		.title(Text.of("Title"))
		.contents(Text.of("Item 1"), Text.of("Item 2"), Text.of("Item 3"))
		.header(Text.of("Header"))
		.footer(Text.of("Footer"))
		.paddingString("p")
		.sendTo(cmdSource);
