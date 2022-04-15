# Custom no op transducer

In previous parts of the documentation, a trasducers has been discribed as a step in a data processing pipeline.
It takes in some data as well as settings and combines these together to create a new data source.
This page describes how to make the most basic custom transducer, the *no-op transducer*.
This is the transducer which performs no actions on the data.

## Trasducer implementation
The following UML diagram demonstrates a custom transducer implementation, this can be generalised to the existing transducers:
![Custom transducer UML](https://i.imgur.com/0OtGpaA.png){.center}
This diagrams give us the following steps required:

1. Adding our new custom transducer type to `TransducerType.java`
2. Creating a new CustomTransducer class that implements `TransducerInterface`
3. Override the execute and getType methods inside the CustomTransducer types
4. Implement these methods
5. Wire up this transducer into a pipeline so that it is executed

## Step 1: adding a new transducer type
The first step is to add the new trasducer to the TransducerType enum.
Navigate to the package `com.tdvf.persistence.entity` and open `TransducerType.java`
The file should look like this:
``` java
public enum TransducerType {

	INITIALIZE("init"),

	MATCH("match"), //user-configurable. needed for fd_discover, example_discover

	FD_DISCOVER("fd_discover"),
	
	FD_REPAIR("repair"), //user-configurable. needs fd_discover, match

	EXAMPLE_DISCOVER("example_discover"), //needs match
	
	EXAMPLE_TRANSFORM("transform"), //user-configurable. needs example_discover, match

	PROFILE("profile"), //user-configurable.

	MAPPING("map"), //user-configurable. needs match, profile
	
	MAPPING_SELECT("select"), //user-configurable. needs mapping

	AGGREGATE("aggregate");

	String name;
	
	private TransducerType(String name) {
		this.name = name;
	}
	
	public String getName() {
		return name;
	}
	
	static public TransducerType lookup(String name) {
		try {
			for (TransducerType type : TransducerType.values()) {
				if (type.getName().equalsIgnoreCase(name)) {
					return type;
				}
			}
			return null;
		} catch (IllegalArgumentException e) {
			return null;
		}
	}

	public String toString() {
		return name;
	}
	
}
```
Change the `AGGEREGATE("aggregate");` line to:
```java
AGGEREGATE("aggregate"),

NO_OP("no_op");
```
This adds the new transducer type `NO_OP`.

## Step 2: creating custom transducer and overriding methods, and implement them.
Inside the transducer folder create a new package called noop.
Inside this package create a new Java file called `NoOpTransducer` with the following content:
```java
package com.tdvf.transducer.noop;

import com.tdvf.client.TransducerInterface;
import com.tdvf.persistence.entity.TransducerType;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Service;

import java.io.File;
import java.util.Map;

@Service
public class NoOpTransducer implements TransducerInterface {
    private static final Logger log = LoggerFactory.getLogger(NoOpTransducer.class);

    @Override
    public void execute(File dataspacePath, Map<String, String> props) {
        log.info("Executed no-op transducer");
    }


    @Override
    public TransducerType getType() {
        return TransducerType.NO_OP;
    }
}
```

This piece of code create the custom no op transducer, overrides the neccessary methods and implements them.