# Set a scenario reporter to dynamically send multiple email attachments

## Use-case

I want to create a Scenario email reporter with multiple Dataset attachments. The list of attachments should be dynamically generated by applying a predicate on the Datasets of the project, e.g. "attach only non-empty datasets".

## Implementation

One possible solution for this problem relies on 2 scenarios: 
- a "sender" Scenario which will be used to actually send the attachment to the recipients,
- a "reporter setup" Scenario that will dynamically edit the reporter of the "sender" Scenario according to the user's predicate, then run it.

## How-to
We assume that you already have a configured email channel on your instance that you will use for your reporter.

1. In your project, create the "sender" Scenario (called `sender_scenario` in the code), add an email reporter on it, then save your changes.
2. Create a new "Custom Python script" Scenario that will be our "reporter setup" Scenario. Copy-paste the code of the `set_reporter_scenario.py` file in it, don't forget to set the `SENDER_SCENARIO` constant accordingly.
3. Run the "reporter setup" Scenario.

## References

* [[doc](https://doc.dataiku.com/dss/latest/python-api/scenarios-inside.html)] Custom Python script Scenarios
* [[doc](https://doc.dataiku.com/dss/latest/python-api/scenarios.html)] Public API reference for Scenarios