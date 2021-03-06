# Installation

Open Monograph Press (OMP) has been developed by the Public Knowledge Project. For general information about OJS and other open research systems, visit the [PKP web site](http://pkp.sfu.ca/).


## Licensing

OMP is licensed under the GNU General Public License v2. See the file
docs/COPYING for the complete terms of this license.

Third parties are welcome to modify and redistribute OMP in entirety or parts
according to the terms of this license. PKP also welcomes patches for
improvements or bug fixes to the software.

## System Requirements

Recommended server requirements:

	* PHP >= 5.3.7
	* MySQL >= 4.1.1 (including MySQL 5.x) or PostgreSQL >= 9.1.5
	* Apache >= 1.3.2x or >= 2.0.4x or Microsoft IIS 6
	* Operating system: Any OS that supports the above software, including
	  Linux, BSD, Solaris, Mac OS X, Windows

As PKP does not have the resources to test every possible combination of
software versions and platforms, no guarantee of correct operation or support
is implied. We welcome feedback from users who have deployed OMP on systems
other than those listed above.


## Recommended Configuration


A secure deployment can be best achieved by using the following policies:

	* Dedicate a database to OMP; use unique credentials to access it.
	  Configure this database to perform automated backups on a regular
	  basis. Perform a manual backup when upgrading or performing
	  maintenance.

	* Configure OMP (config.inc.php) to use SHA1 hashing rather than MD5.

	* Configure OMP (config.inc.php) to use force_ssl_login so that
	  authenticated users communicate with the server via HTTPS.

	* Install OMP so that the files directory is NOT a subdirectory of
	  the OMP installation and cannot be accessed directly via the web
	  server. Restrict file permissions as much as possible. Automated
	  backups of this directory should be roughly synchronized with
	  database backups.

## Download

OMP can be downloaded from the [Public Knowledge Project web site](http://pkp.sfu.ca/).

## Installation

Please review this document and the RELEASE document prior to installing OMP.

To install OMP:

	1. Extract the OMP archive to the desired location in your web
	   documents directory.
	
	2. Make the following files and directories (and their contents)
	   writeable (i.e., by changing the owner or permissions with chown or
	   chmod):
	   
	     * config.inc.php (optional -- if not writable you will be prompted
	       to manually overwrite this file during installation)
	     * public
	     * cache
	     * cache/t_cache
	     * cache/t_config
	     * cache/t_compile
	     * cache/_db
	
	3. Create a directory to store uploaded files (submission files, etc.)
	   and make this directory writeable. It is recommended that this
	   directory be placed in a non-web-accessible location (or otherwise
	   protected from direct access, such as via .htaccess rules).
	   
	4. Review and apply the patches recommended for your version of OMP.

	   The Public Knowledge Project development team maintains a publicly-
           available list of recommended patches for each release. These will
           add no new functionality and will typically consist of small,
           easy-to-read patches for specific issues. A Recommended Patches list
           for your version of OMP can be found on the PKP development wiki:

	       <http://pkp.sfu.ca/wiki/index.php/OMP_Recommended_Patches>

	   To apply a recommended patch, open the bug report and download the 
	   attached patch file(s). (Note that bug reports can quite often
           include a number of patches, some relevant to the application (ie.
           OMP) and version you are running, and some not. Ensure that you
           download all and only the patches specific to your application and
           version.) For each patch you download, first attempt a dry-run
           application of the patch, to ensure that it applies cleanly: 

	       $ patch -p1 --dry-run < PATCH_FILE

	   If the patch applies cleanly, then run the following command, which 
	   will actually apply the patch: 

	       $ patch -p1 < PATCH_FILE

	   "PATCH_FILE" should be replaced with the path to the patch file that 
	   was downloaded, e.g. "6276-omp.patch".

	5. Open a web browser to <http://yourdomain.com/path/to/omp/> and
	   follow the on-screen installation instructions.
	   
	   Alternatively, the command-line installer can be used instead by
	   running the command "php tools/install.php" from your OMP directory.
	   (Note: with the CLI installer you may need to chown/chmod the public
	   and uploaded files directories after installation, if the Apache
	   user is different from the user running the tool.)

	6. Recommended additional steps post-installation:
	
	     * Review config.inc.php for additional configuration settings
	     * Review the FAQ document for frequently asked technical and
	       server configuration questions.
	     * Review the plugins/generic/usageStats/README file for additional
	       statistics processing requirements/configuration.

## Localization

To add support for other languages, the following sets of XML files must be
localized and placed in an appropriately named directory (using ISO locale 
codes, e.g. "fr_FR", is recommended):

	* locale/en_US
	* help/en_US
	* registry/locale/en_US
	* plugins/[plugin category]/[plugin name]/locale, where applicable

The only critical files that need translation for the system to function
properly are found in locale/en_US and registry/locale/en_US.

New locales must also be added to the file registry/locales.xml, after which
they can be installed in the system through the site administration web
interface.
	
Translations can be contributed back to PKP for distribution with future
releases of OMP.

