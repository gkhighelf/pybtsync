Tutorial and Walkthrough 
====================================

Refer to the github page on how to install the module `pybitsync <https://github.com/tiagomacarios/pybtsync>`_

Getting Started
---------------

.. note:: You dont need to have BitTorrent Sync running to follow this introduction.

To make things easier set you `BitTorrent sync API key <http://www.bittorrent.com/sync/developers>`_ to a environment variable. Using python only this can be done using:

::

	>>> import os
	>>> os.environ['PYBTSYNC_APIKEY'] = '****'

First thing you will need to import the module:

::

	>>> import pybtsync
	
After that you will need to start a BitTorrent Sync process to be able to communicate with it. To do that create a :class:`~pybtsync.BTSyncProcess` object.
When creating a :class:`~pybtsync.BTSyncProcess` object for the first time the module will download the proper binaries for the OS + architecture.
Since a :class:`~pybtsync.BTSyncProcess` object expects a configuration file it is easier to use the :func:`~pybtsync.BTSyncProcess.with_settings` class method to
automatically create all the necessary configuration files:

::

	>>> btsync_process = pybtsync.BTSyncProcess.with_settings()
	
.. note:: If you are using windows the line above will request for firewall access.

To get access to the API you will need to create a :class:`BTSync` object by using:

::

	>>> btsync = BTSyncProcess.BTSync()

Using :class:`~pybtsync.BTSyncProcess` to create :class:`~pybtsync.BTSync` ensures that all the necessary settings are correctly set on the background.

To check if everything is working correctly just try to get a listing of the folders:

::

 	>>> btsync.folders
	[]
	
Full set of commands on this getting started:

::

	import pybtsync
	btsync_process = pybtsync.BTSyncProcess.with_settings()
	btsync = btsync_process.BTSync()
	btsync.folders