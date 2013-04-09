<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!--  Include the core schedule processor - update href path! -->
    <xsl:include href=".../class-schedule"/>

    <xsl:template match="/system-data-structure">
        <link href="http://webcore.unm.edu/v1/css/jquery-ui.css" media="screen" rel="stylesheet"
            type="text/css"/>
        <script src="https://webcore.unm.edu/v1/javascript/jquery-ui.min.js"/>
        <script>
            $(function() {
        
                $( ".accordion" ).accordion({
                    autoHeight: false,
                    navigation: true,
                    active: false, 
                    collapsible: true,
                    header: 'h5'
                });
                
                $('#la-schedules a:first').tab('show');
                $( ".la-class-schedules" ).each(function() {
                      $(this).find("a:first").tab('show');
                });   
            });
        </script>
        <h2><xsl:value-of
                select="feed/content/schedule-feed/content/unmschedulesemester/campus/@name"/> Class
            Schedule</h2>

        <p>Schedule as of <xsl:call-template name="format-date">
                <xsl:with-param name="date"
                    select="feed/content/schedule-feed/content/unmschedule/@pubdate"/>
                <xsl:with-param name="mask">longDate</xsl:with-param>
            </xsl:call-template>
        </p>
        <ul class="nav nav-pills" id="la-schedules">
            <xsl:apply-templates mode="tabs" select="feed/content[unmschedule/semester]"/>
        </ul>
        <div class="tab-content">
            <xsl:apply-templates mode="panels" select="feed/content[unmschedule/semester]"/>
        </div>
    </xsl:template>

    <xsl:template match="content" mode="tabs">
        <li>
            <a data-toggle="tab" href="#tab-{position()}">
                <xsl:value-of select="unmschedule/semester/@name"/>
            </a>
        </li>
    </xsl:template>

    <xsl:template match="content" mode="panels">
        <div class="tab-pane" id="tab-{position()}">
            <xsl:apply-templates select="unmschedule"/>
        </div>
    </xsl:template>

    <xsl:template name="format-date"/>

</xsl:stylesheet>
