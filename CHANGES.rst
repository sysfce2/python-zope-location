Changes
=======

4.0.4 (unreleased)
------------------

- Add a page to the docs on hacking ``zope.location``.

- Note additional documentation dependencies.

- Claim support for Python 3.5.


4.0.3 (2014-03-19)
------------------

- Added Python 3.4 support.

- Updated ``boostrap.py`` to version 2.2.


4.0.2 (2013-03-11)
------------------

- Changed the behavior of ``LocationProxy``'s ``__setattr__()`` to correctly
  behave when dealing with the pure Python version of the ``ProxyBase``
  class. Also added a test suite that fully tests the pure Python proxy
  version of the ``LocationProxy`` class.


4.0.1 (2013-02-19)
------------------

- Added Python 3.3 support.

4.0.0 (2012-06-07)
------------------

- Removed backward-compatibility imports:

  - ``zope.copy.clone`` (aliased as ``zope.location.pickling.locationCopy``)

  - ``zope.copy.CopyPersistent`` (aliased as
    ``zope.location.pickling.CopyPersistent``).

  - ``zope.site.interfaces.IPossibleSite`` (aliased as
    ``zope.location.interfaces.IPossibleSite``).

- Added Python 3.2 support.

- Made ``zope.component`` dependency optional.  Use the ``component`` extra
  to force its installation (or just require it directly).  If
  ``zope.component`` is not present, this package defines the ``ISite``
  interface itself, and omits adapter registrations from its ZCML.

- Added support for PyPy.

- Added support for continuous integration using ``tox`` and ``jenkins``.

- 100% unit test coverage.

- Added Sphinx documentation:  moved doctest examples to API reference.

- Added 'setup.py docs' alias (installs ``Sphinx`` and dependencies).

- Added 'setup.py dev' alias (runs ``setup.py develop`` plus installs
  ``nose`` and ``coverage``).

- Replaced deprecated ``zope.component.adapts`` usage with equivalent
  ``zope.component.adapter`` decorator.

- Replaced deprecated ``zope.interface.implements`` usage with equivalent
  ``zope.interface.implementer`` decorator.

- Dropped support for Python 2.4 and 2.5.


3.9.1 (2011-08-22)
------------------

- Added zcml extra as well as a test for configure.zcml.


3.9.0 (2009-12-29)
------------------

- Moved LocationCopyHook related tests to zope.copy and remove a test
  dependency on that package.

3.8.2 (2009-12-23)
------------------

- Fixed a typo in the configure.zcml.

3.8.1 (2009-12-23)
------------------

- Removed dependency on zope.copy: the LocationCopyHook adapter is registered
  only if zope.copy is available.

- Use the standard Python doctest module instead of zope.testing.doctest, which
  has been deprecated.

3.8.0 (2009-12-22)
------------------

- Adjusted to testing output caused by new zope.schema.

3.7.1 (2009-11-18)
------------------

- Moved the IPossibleSite and ISite interfaces to zope.component as they are
  dealing with zope.component's concept of a site, but not with location.

3.7.0 (2009-09-29)
------------------

- Added getParent() to ILocationInfo and moved the actual implementation here
  from zope.traversal.api, analogous to getParents().

- Actually removed deprecated PathPersistent class from
  zope.location.pickling.

- Moved ITraverser back to zope.traversing where it belongs conceptually. The
  interface had been moved to zope.location to invert the package
  interdependency but is no longer used here.

3.6.0 (2009-08-27)
------------------

- New feature release: deprecated locationCopy, CopyPersistent and
  PathPersistent from zope.location.pickling. These changes were already part
  of the 3.5.3 release, which was erroneously numbered as a bugfix relese.

- Removed dependency on zope.deferredimport, directly import deprecated modules
  without using it.

3.5.5 (2009-08-15)
------------------

- Add zope.deferredimport as a dependency as it's used directly by
  zope.location.pickling.

3.5.4 (2009-05-17)
------------------

- Add ``IContained`` interface to ``zope.location.interfaces`` module.
  This interface was moved from ``zope.container`` (after
  ``zope.container`` 3.8.2); consumers of ``IContained`` may now
  depend on zope.location rather than zope.container to reduce
  dependency cycles.

3.5.3 (2009-02-09)
------------------

- Use new zope.copy package for implementing location copying. Thus
  there's changes in the ``zope.locaton.pickling`` module:
  
   * The ``locationCopy`` and ``CopyPersistent`` was removed in prefer
     to their equivalents in zope.copy. Deprecated backward-compatibility
     imports provided.
   
   * The module now provides a ``zope.copy.interfaces.ICopyHook`` adapter
     for ``ILocation`` objects that replaces the old CopyPersistent
     functionality of checking for the need to clone objects based on
     their location.

3.5.2 (2009-02-04)
------------------

- Split RootPhysicallyLocatable adapter back from LocationPhysicallyLocatable,
  because the IRoot object may not always provide ILocation and the code
  for the root object is also simplier. It's basically a copy of the
  RootPhysicallyLocatable adapter from zope.traversing version 3.5.0 and
  below with ``getParents`` method added (returns an empty list).

3.5.1 (2009-02-02)
------------------

- Improve test coverage.

- The new ``getParents`` method was extracted from ``zope.traversing``
  and added to ILocationInfo interface in the previous release. Custom
  ILocationInfo implementations should make sure they have this method
  as well. That method is already used in ``zope.traversing.api.getParents``
  function.

- Make ``getName`` of LocationPhysicallyLocatable always return empty
  string for the IRoot object, like RootPhysicallyLocatable from
  ``zope.traversing`` did. So, now LocationPhysicallyLocatable is
  fully compatible with RootPhysicallyLocatable, making the latter one
  obsolete.

- Change package mailing list address to zope-dev at zope.org instead
  of retired zope3-dev at zope.org.

3.5.0 (2009-01-31)
------------------

- Reverse the dependency between zope.location and zope.traversing. This
  also causes the dependency to various other packages go away.

3.4.0 (2007-10-02)
------------------

- Initial release independent of the main Zope tree.
