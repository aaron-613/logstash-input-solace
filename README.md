# Logstash Input Plugin to Solace

A starter project, work-in-progress, for reading data off Solace PubSub+ event broker, and injecting into Logstash.  It is based on https://github.com/logstash-plugins/logstash-input-java_input_example and https://www.elastic.co/guide/en/logstash/current/java-input-plugin.html.  It is a JCSMP Java API alternative to https://www.elastic.co/guide/en/logstash/current/plugins-inputs-jms.html.  

Right now only supports subscribing Directly to topics, can't be used yet for Guaranteed messaging.

## Building

```
./gradlew clean gem
```

Then use the `logstash-plugin` utility in your Logstash distribution to import the generated gem file.

## Example config:

```
input {
  solace {
    host => "192.168.42.35"
    vpn => "stats"
    username => "statspump"
    password => "password"
    topics => [ "#STATS/>", "solace/*" ]
  }
}
```

