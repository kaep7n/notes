# configuration

## example configuration

the following config configures NLog to log to a file and prints colored messages on a console

```markup
<?xml version="1.0" encoding="utf-8" ?>
<nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">

  <targets>
    <target
        name="logfile"
        xsi:type="File"
        fileName="file.log"
        layout="${longdate}|${pad:padding=5:inner=${level:uppercase=true}}|${message} ${onexception:${newline}  ${exception:format=ToString}}" />
    <target
        name="console"
        xsi:type="Console"
        layout="${longdate}|${pad:padding=5:inner=${level:uppercase=true}}|${message} ${onexception:${newline}  ${exception:format=ToString}}" />

    <target
        name="colourconsole"
        xsi:type="ColoredConsole"
        layout="${longdate}|${pad:padding=5:inner=${level:uppercase=true}}|${message} ${onexception:${newline}  ${exception:format=ToString}}"
        useDefaultRowHighlightingRules="true">

        <highlight-word backgroundColor="Yellow" foregroundColor="Black" ignoreCase="false" text="ERROR" wholeWords="true" />
        <highlight-word backgroundColor="Red" foregroundColor="White" ignoreCase="false" text="FATAL" wholeWords="true" />
    </target>

  </targets>

  <rules>
    <logger name="*" minlevel="Info" writeTo="logfile" />
    <logger name="*" minlevel="Trace" writeTo="colourconsole" />
  </rules>
</nlog>
```

