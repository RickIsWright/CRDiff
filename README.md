<p><!-- #######  YAY, I AM THE SOURCE EDITOR! #########--></p>
<h1>CRDiff</h1>
<p>CRDiff is a program that serializes the binary Crystal reports .rpt files to human readable .json files, and works in conjunction with your favorite text diff tool. If your tool is configurable to use file transforms/converters, it works even better.</p>
<h1><a id="user-content-installation" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#installation" aria-hidden="true"></a>Installation</h1>
<p>The published location is \\aus2-odx-dfs01.pdsenergy.local\devTools\CRDiff</p>
<p>Copy the contents to the local folder of your choice (referred to below as &lt;CRDiff Path&gt;) - Having that folder in your PATH environment variable can be helpful.</p>
<p>You may get a message "Are you sure you want to run this software?"</p>
<ul>
<li>Uncheck "Always ask before opening this file" and</li>
<li>press "Run"</li>
</ul>
<p>If when CRDiff.exe is run with no parameters, you don't see a valid CR Version displayed, you may need to install the Crystal Reports Runtime, available in the Crystal Reports Runtime folder.</p>
<h1><a id="user-content-usage" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#usage" aria-hidden="true"></a>Usage:</h1>
<ul>
<li>CRDiff.exe DiffAppPath.exe
<ul>
<li>Save your diff tool's path in CRDiff's config file.</li>
</ul>
</li>
<li>CRDiff.exe ReportFilename.rpt
<ul>
<li>Serialize the report to a json file of the same name and location but with .json extension.</li>
</ul>
</li>
<li>CRDiff.exe ReportFilename.rpt, ReportFilename2.rpt
<ul>
<li>Serialize the two reports to json and pass the json files to your diff tool. Once you close your text diff tool, CRDiff will delete the json files (if they hadn't already existed). If you haven't set a text diff path above, you will be prompted for one.</li>
</ul>
</li>
<li>CRDiff.exe DiffAppPath.exe ReportFilename1.rpt ReportFilename2.rpt
<ul>
<li>Same as above, but DiffAppPath.exe is used instead of what is saved in config.</li>
</ul>
</li>
<li>CRDiff.exe ReportFilename.rpt, TempFilename(.json)
<ul>
<li>Serialize ReportFilename.rpt to TempFilename (provided by your configurable text diff tool, which is responsible for cleaning up after itself).</li>
</ul>
</li>
<li>Parameters:
<ul>
<li>DiffAppPath - path to external differencing application .exe file that can compare two text files</li>
<li>ReportFilename1 - path to first .rpt file to be serialized to json, or it can be an existing report.json file</li>
<li>ReportFilename2 - path to second .rpt file to be serialized to json (or existing .json file) and compared with first file</li>
<li>TempFilename - path to a temporary file that will likely be deleted after use.</li>
</ul>
</li>
</ul>
<h1><a id="user-content-configuration" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#configuration" aria-hidden="true"></a>Configuration</h1>
<h2><a id="user-content-compareit" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#compareit" aria-hidden="true"></a>CompareIt!</h2>
<p>Open CompareIt!, open Tools/Options, and select Converters. Press "Add", and specify Name: "Crystal Reports", Mask: "*.rpt", Command: "&lt;CRDiff path&gt;CRDiff.exe", Arguments: "{$Source_File} {$Converted_File}"</p>
<h2><a id="user-content-beyond-compare" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#beyond-compare" aria-hidden="true"></a>Beyond Compare</h2>
<p>In Tools, File Formats..., press "+" and select Text Format. In the General tab, specify Mask: "*.rpt". In the Conversion tab, specify "External program (Unicode filenames)", Loading: "&lt;CRDiff path&gt;CRDiff.exe %s %t", check Disable editing, then Save.</p>
<h2><a id="user-content-tortoisegit" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#tortoisegit" aria-hidden="true"></a>TortoiseGit</h2>
<p>In Settings, Diff Viewer, click Advanced, Add..., and specify Extension: ".rpt", External Program: "&lt;CRDiff path&gt;CRDiff.exe &lt;path to your text compare tool&gt; %base %mine"</p>
<h2><a id="user-content-others" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#others" aria-hidden="true"></a>Others</h2>
<p>TBA</p>
<h1><a id="user-content-features" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#features" aria-hidden="true"></a>Features</h1>
<ul>
<li>Checks file extension, and if it is not .rpt, file passes directly to text diff tool.</li>
<li>Serializes many of the report details we want to be able to compare into a text file, like
<ul>
<li>Command query</li>
<li>element dimensions and settings</li>
<li>subreports</li>
</ul>
</li>
<li>Save serialized files and pass to a text diff tool</li>
<li>Clean-up (delete) temp files after text diff tool is closed.</li>
</ul>
<h1><a id="user-content-still-to-implement" class="anchor" href="https://github.transzap.com/oildex/CRDiff/blob/master/README.md#still-to-implement" aria-hidden="true"></a>Still to Implement</h1>
<ul>
<li>Need to output
<ul>
<li>element suppression formulas (and other formulas for elements)</li>
<li>sub-textbox formatting (ie font changes, coloring, tab settings, etc)</li>
<li>"Lock Position"</li>
<li>"change number sign"</li>
<li>Page Setup (ie Printer, margins)</li>
<li>"Keep Data" setting</li>
</ul>
</li>
</ul>
