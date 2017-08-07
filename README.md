# NLog.RabbitMQ.Extension
NLog Extension for RabbitMQ

	
~~~ xml
<nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:haf="https://github.com/haf/NLog.RabbitMQ/raw/master/src/schemas/NLog.RabbitMQ.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      internalLogToConsole="true">

  <extensions>
    <add assembly="NLog.RabbitMQ.Extension" />
  </extensions>

  <targets async="true">    
    <target name="RabbitMQTarget"
            xsi:type="RabbitMQ"
            username="guest"
            password="guest"
            hostname="localhost"
            exchange="app-logging"
            port="5672"
            topic="DemoApp.Logging.{0}"
            vhost="/"
            durable="true"
            appid="NLog.RabbitMQ.DemoApp"
            maxBuffer="10240"
            heartBeatSeconds="3"
            useJson="true"            
    />
  </targets>

  <rules>
    <logger name="*" minlevel="Trace" writeTo="RabbitMQTarget"/>
  </rules>

</nlog>
~~~
