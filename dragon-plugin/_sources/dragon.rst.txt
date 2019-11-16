
=====================
The DRAGON Interface
=====================

Software Description
============================================

The :py:class:`DRAGON Interface <terrapower.physics.neutronics.dragon.dragonInterface.DragonInterface>`
is responsible for writing DRAGON input files, executing them,
and producing microscopic cross sections in the form of ISOTXS files.


Capabilities
------------
DRAGON is a lattice physics tool developed and owned by École Polytechnique de Montréal.
It primarily supports thermal reactors but some success has been
had with it as tool for fast reactor analysis.

The DRAGON interface produces an microscopic cross sections in the form of an ISOTXS
file. The default execution produces a 0D model of the block with a critical buckling
calculation.

The DRAGON interface send various settings (such as if critical buckling is requested) 
and ARMI (objects such as block) to a template, and the template is filled out to create
the input file

DRAGON can also model more complex geometry, but users are responsible for creating
their own template to model the needed geometry

Interaction
-----------
* To turn DRAGON on as the lattice physics tool the setting ``xsKernel`` must be set 
  to ``DRAGON``.
* For DRAGON to run, the location of your DRAGON executable must be known. The location 
  of your DRAGON executable can either be added to your path, or you can put the full
  path of your executable in the setting ``dragonExePath``.
* The setting ``dragonDataPath`` must point to the full path of your nuclear data file
  for your run. It is important to leave the file with the detail names, so ARMI can
  determine which nuclides must be expanded from elementals to isotopics. E.G.,
  expanding elemental Iron into the 4 naturally occurring isotopes.
* The setting ``dragonTemplateHelper`` can be used to point to your own template helper
  class. This template helper class should inherit from ``DragonTemplateHelper``, but
  will allow you to point to your own template, and perform any needed calculations to
  send into the template. This is the primary way the DRAGON interface supports custom
  geometry.
* After DRAGON runs, all ISOTXS files created will be merged into one ISOTXS file called
  `ISOTXS`.

Limitations
-----------
* The DRAGON interface currently only supports ENDF/B-VII.0/1 and ENDF/B-VIII.0. The
  libraries must remain their default name.
* The DRAGON interface was initially developed to serve as an example for how to develop
  a plugin, and to provide a rudimentary interface to DRAGON. As such, it has many
  limitations and numerous simplifying assumption. The reader is encouraged to improve
  these as they wish.

Structure
---------
The DRAGON interface is composed of:

* An interface class responsible for creating new cross sections at the beginning of
  each cycle.
* A writer class which is responsible for writing a DRAGON input file.
* A template helper class which is responsible for interacting with the template.
* An executor class, which is responsible for executing DRAGON.
