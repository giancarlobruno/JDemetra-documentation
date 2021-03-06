---
layout: left-menu
title: Simple seasonal adjustment of multiple time series
tagline: technical documentation for JDemetra+ using GitHub Pages
description: Basics
---
This scenario is intended for a seasonal adjustment of a dataset of
multiple time series. It is especially useful when hundreds of series
need to be processed and the quality of their adjustment assessed. This
scenario can be used in a regular production process. As it does not
focus on individual series, it is not recommended for an adjustment of
key indicators that requires a detailed analysis of results and refining
of the seasonal adjustment settings. The scenario shows the steps of the
data generating process for multiple series, with references to
appropriate parts of the *JDemetra+ Reference Manual* (2017) for more
detailed explanations. Although this case study is intended for the
datasets, it can be also performed for a single time series, provided
that the analysis is done in a multi-document.

1.  Go to the main menu and follow the path: *Statistical methods* →
    *Seasonal adjustment* → *Multi Processing* → *New* to open a
    multi-document.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image19.jpg)

	{: .text-center.small}

	**Launching a seasonal adjustment for a dataset**

2.  JDemetra+ opens an empty window (default name: *SAProcessing-1*). By
    default, one of the pre-defined specifications (see the *JDemetra+
    Reference Manual* (2017), section 5.1 will be used for a seasonal
    adjustment of a dataset. To change the specification used for an
    adjustment in the current document, click on the button marked in
    the picture below. This will provide you with the alternative
    methods of adjustment. To change the settings for a pre-defined
    specification used by default for an adjustment, see *JDemetra+
    Reference Manual* (2017), section 3.4.7).

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image20.jpg)

	{: .text-center.small}

	**Default window for seasonal adjustment process for a dataset**

3.  The list available from the *SAProcessing* window includes the
    pre-defined specifications and the user-defined specifications (if
    any). For a description of the user-defined specifications see
    3.2.1.1). Click on the specification that will be used for a
    seasonal adjustment (in the example below *RSA4* is selected).

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image21.jpg)

	{: .text-center.small}

	**Choice of the specification**

4.  Drag and drop series from the *Providers* window to the
    *SAProcessing* window. You can drag and drop individual series or an
    entire dataset (i.e. a set of series that have been imported
    together, e.g. series from the same Excel file). It is possible to
    drag and drop the same series several times. It allows the user to
    apply different specifications to the same time series in order to
    compare the results. The series visible in the *SAProcessing* window
    are not seasonally adjusted yet (*Status* -- \"Unprocessed\").
    Adjustment will be performed using *RSA4* specification. For a newly
    created *SAProcessing* window the *Estimation* column is always set
    to *Concurrent*, which means that previous results for these time
    series will not be taken into account once this seasonal adjustment
    is launched (as they do not exist). However, a seasonal adjustment
    processing window may be saved and re-launched in the next session
    of JDemetra+. Then the user can decide if and how the previous
    results are used in the current session. At this stage the
    *Priority*, *Quality* and *Warnings* columns are empty as seasonal
    adjustment has not yet been performed.


	The revisions issue is discussed in depth in 3.2.2.2.
	
	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image22.jpg)

	{: .text-center.small}

	**Adding the series to the multi document**

5.  Once the user clicks on the start button (the button with a green
    arrow) the time series are processed, the statuses are updated and
    some information about the quality of the adjustments and possible
    problems are displayed in the *Warnings* column as exclamation
    marks.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image23.jpg)

	{: .text-center.small}

	**The *Start* button**

6.  Generally, the warnings are put forward for short series,
    non-decomposable models (SEATS) or when the differenced series do
    not show seasonal peaks. Information on the warnings is displayed
    when the cursor hovers over an exclamation mark.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image24.jpg)

	{: .text-center.small}

	**The results of a seasonal adjustment process**

7.  When the user clicks on an individual time series in the
    *SAProcessing* window, detailed results are displayed in the panel
    below the list of the series. By default, a summary of results is
    displayed, accompanied by two graphs: original data,
    seasonally-adjusted series and the trend-cycle on the left and SI
    ratio values on the right. These diagnostics and graphs are
    discussed in *JDemetra+ Reference Manual* (2017), Chapter 4 and
    Chapter 5 (see 5.2.2 for X-13ARIMA-SEATS, 5.2.1 for TRAMO/SEATS).

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image25.jpg)

	{: .text-center.small}

	**The inspection of the seasonal adjustment results for a chosen time series**

8.  The *Main results* panel provides information on the quality of the
    adjustment. Study the diagnostic section using the vertical
    scrollbar. The results are marked in green, yellow or red, depending
    on the result of a statistical test used. Those in green denote that
    the problematic characteristic has not been detected (e.g. lack of
    normality of residuals, the autocorrelation in residuals). The
    outcome in yellow means that the test outcome is uncertain. The
    outcomes in red denote cases where an issue should be addressed.
    Hence, test statistics will indicate the need to improve the model.
    Ideally, the model should be improved so that no test statistics
    indicate uncertainties is the results.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image26.jpg)

	{: .text-center.small}

	**The diagnostics results -- simple seasonal adjustment of a multiple time series**

9.  To explore the results, expand the tree on the left and click on the
    desired node. Here *out-of-sample test* was chosen (see the
    *JDemetra+ Reference Manual* (2017), 4.2.3).

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image27.jpg)

	{: .text-center.small}

	**Out-of-sample test results**

10. The specifications used for a seasonal adjustment of an individual
    series can be changed by clicking on the *Specifications* button as
    described in the section 3.1.1.

11. To export the output for a whole dataset, select the *Output* item
    from the *SAProcessing* menu.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image28.jpg)

	{: .text-center.small}

	**The *SAProcessing* menu**

12. Expand the \"+\" menu and choose an appropriate data format (here
    Excel has been chosen). It is possible to save the results in TXT,
    XLS, CSV, and CSV matrix formats. Note that the available content of
    the output depends on the output type (see the *JDemetra+ Reference
    Manual* (2017), 7.7 for more details).

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image29.jpg)

	{: .text-center.small}

	**Exporting data to an Excel file**

13. Specify export details and click *OK*. For more output options see
    3.2.2.1.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image30.jpg)

	{: .text-center.small}

	**Defining an export details**

14. To save the workspace that includes the results in the processing
    window (named *SAProcessing-1* in the example) select *Save
    Workspace As...* item from the *File* menu.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image31.jpg)

	{: .text-center.small}

	**Saving the workspace**

15. Enter the location and the workspace name and click *Save.*

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image31_1.jpg)

	{: .text-center.small}

	**Saving details**

16. The document is visible in the *Workspace* window under the
    multi-documents branch.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image32.jpg)

	{: .text-center.small}

	**The content of the context menu for a multi-document**

17. The document can be opened, deleted or renamed from the context
    menu. The user can also add comments to the document (see 3.1.1).
    When JDemetra+ is launched again the saved workspace can be opened
    and the multi-document can be run again.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image33.jpg)

	{: .text-center.small}

	**Reopening the multi-document**

18. The seasonal adjustment can be refreshed by clicking on the green
    arrow button or by choosing the refresh option from *SAProcessing*
    menu (note that the name of this main menu item corresponds to the
    name of the processing window). Refreshing policies are presented in
    3.2.2.2.

	{: .text-center.image-wrapper}

	![Text](/assets/img/user-guide/UG_SSA_image34.jpg)

	{: .text-center.small}

	**Refreshing option**
