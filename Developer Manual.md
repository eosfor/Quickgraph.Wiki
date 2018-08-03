### Developer Manual

#### Branches

* Requires Visual Studio 2010
* 2.0: deprecated.
* 3.0:
	* .NET 2.0:
		* Use the {{Release20}} configuration.
	* .NET 3.5:
		* Use the {{Debug}}, {{Release}} configurations.
	* .NET 3.5 + Code Contracts:
		* Use the {{DebugContracts}} configuration.

As you may notice, the same codebase is used for .net 2.0 and .net 3.5. This means that anything that belongs to {{System.Core}} must be duplicated in QuickGraph conditionally. In that sense,
	* do not use Linq. If you do, add the required method in the {{Enumerable}} type.
	* put the {{this}} of extenion methods in an {{#ifdef}} region.
{{
#if !NET20
    this
#endif
}}

#### External tools

* Code Contracts [http://research.microsoft.com/contracts](http://research.microsoft.com/contracts) (optional)
* Pex [http://research.microsoft.com/Pex/downloads.aspx](http://research.microsoft.com/Pex/downloads.aspx) (required)

#### Getting the source code

* Using the svn bridge is the recommended method to sync the sources.