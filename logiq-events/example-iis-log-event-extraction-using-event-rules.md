# Example IIS Log Event Extraction Using Event Rules

Ingested IIS Log events fields can be fully parsed using the pre-built LOGIQ.ai pack rules.   The section illustrates how one customizes it for its need.  Other pre-built packs can also be used in the same way to tailor for the needs.

The first step is to click on the "rule" label at the top-right UI to get to the pack windows.  Select and select the IIs block at the bottom right to get to the IIS rule page.

![](../.gitbook/assets/pack-2022-02-21\_13-29-49.jpg)

Once at the rule page, select and edit the first rule.   Once in the rule-edit screen, click the top "extract" rule-type, copy and store the regex rule at the bottom.   This new rule will need to use the newly copied regex.

![](../.gitbook/assets/copy-iis-2022-02-21\_13-32-11.jpg)

Create the new ruleset by clicking the upper right "new Rule" button.   Below is the new rule based on the existing regex extract.  Notice that both namespace and app\_name need to be configured. &#x20;

![](../.gitbook/assets/new-iis-rule-2022-02-21\_13-38-43.jpg)

Once all the new blanks are filled and validated, the "create rule" button at the bottom right can be saved and applied for the log events.   The new rule is created and activated after exiting the rule creation page, and the screen image s shown below.

![](../.gitbook/assets/activate-iis-rule-2022-02-21\_13-39-25.jpg)
