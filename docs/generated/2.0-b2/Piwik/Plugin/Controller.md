<small>Piwik\Plugin</small>

Controller
==========

Base class of all plugin Controllers.

Description
-----------

Plugins that wish to add display HTML should create a Controller that either
extends from this class or from [ControllerAdmin](#). Every public method in
the controller will be exposed as a controller action.

Learn more about Piwik&#039;s MVC system [here](#).

### Examples

**Defining a controller**

    class Controller extends \Piwik\Plugin\Controller
    {
        public function index()
        {
            $view = new View(&quot;@MyPlugin/index.twig&quot;);
            // ... setup view ...
            echo $view-&gt;render();
        }
    }

**Linking to a controller action**

    &lt;a href=&quot;?module=MyPlugin&amp;action=index&amp;idSite=1&amp;period=day&amp;date=2013-10-10&quot;&gt;Link&lt;/a&gt;


Methods
-------

The abstract class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`getDefaultAction()`](#getDefaultAction) &mdash; Returns the name of the default method that will be called when visiting: index.php?module=PluginName without the action parameter.
- [`setHostValidationVariablesView()`](#setHostValidationVariablesView) &mdash; Checks if the current host is valid and sets variables on the given view, including:
- [`setPeriodVariablesView()`](#setPeriodVariablesView) &mdash; Sets general period variables on a view, including:  - **displayUniqueVisitors** - Whether unique visitors should be displayed for the current                               period.
- [`redirectToIndex()`](#redirectToIndex) &mdash; Helper method used to redirect the current http request to another module/action.
- [`getCalendarPrettyDate()`](#getCalendarPrettyDate) &mdash; Returns a prettified date string for use in period selector widget.

### `__construct()` <a name="__construct"></a>

Constructor.

#### Signature

- It is a **public** method.
- It does not return anything.

### `getDefaultAction()` <a name="getDefaultAction"></a>

Returns the name of the default method that will be called when visiting: index.php?module=PluginName without the action parameter.

#### Signature

- It is a **public** method.
- It returns a(n) `string` value.

### `setHostValidationVariablesView()` <a name="setHostValidationVariablesView"></a>

Checks if the current host is valid and sets variables on the given view, including:

#### Description

- **isValidHost** - true if host is valid, false if otherwise
- **invalidHostMessage** - message to display if host is invalid (only set if host is invalid)
- **invalidHost** - the invalid hostname (only set if host is invalid)
- **mailLinkStart** - the open tag of a link to email the super user of this problem (only set
                      if host is invalid)

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$view`
- It does not return anything.

### `setPeriodVariablesView()` <a name="setPeriodVariablesView"></a>

Sets general period variables on a view, including:  - **displayUniqueVisitors** - Whether unique visitors should be displayed for the current                               period.

#### Description

- **period** - The value of the **period** query parameter.
- **otherPeriods** - `array(&#039;day&#039;, &#039;week&#039;, &#039;month&#039;, &#039;year&#039;, &#039;range&#039;)`
- **periodsNames** - List of available periods mapped to their singular and plural translations.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$view`
- It does not return anything.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; if the current period is invalid.

### `redirectToIndex()` <a name="redirectToIndex"></a>

Helper method used to redirect the current http request to another module/action.

#### Description

If specified, will also change the idSite, date and/or period query parameters.

This function will exit immediately after executing.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$moduleToRedirect`
    - `$actionToRedirect`
    - `$websiteId`
    - `$defaultPeriod`
    - `$defaultDate`
    - `$parameters`
- It does not return anything.

### `getCalendarPrettyDate()` <a name="getCalendarPrettyDate"></a>

Returns a prettified date string for use in period selector widget.

#### Signature

- It is a **public static** method.
- It accepts the following parameter(s):
    - `$period`
- It returns a(n) `string` value.
