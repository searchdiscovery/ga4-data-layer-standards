# Frequently Asked Questions

<details>
  <summary>Are there any general naming conventions?</summary>
  
  ## Event Names
  1. Always use lowercase [snake_case](https://en.wikipedia.org/wiki/Snake_case)
  2. Always prefer an event name with a combination of subject and verb instead of a single verb
  3. The noun/subject should always come before event action/verb
  3. Verbs should always be present tense

  Examples
  1. `form_start`, not `Form Start` or `Form_Start` or `form-start`
  2. `form_start`, not `start`
  3. `form_view`, not `view_form`
  4. `form_complete`, not `form_completed`

  ## Parameter names
  1. Always use lowercase [snake_case](https://en.wikipedia.org/wiki/Snake_case)
  2. Tend towards generic parameter names instead of namespaced/prefixed to save CD slots whenever possible. If there is already a parameter on another event that could be used, consider using it. Yes, this is in direct contrast to the event name practice of including subjects. However, parameters are under different constraints from events. See "Why aren't all of the parameters namespaced/prefixed?" below for additional details.
</details>

<details>
  <summary>Why do we need standards anyway?</summary>
  
  ## Standardizing SQL queries and dashboards
  Using consistent event names makes it a whole easier on analysts and data engineers to be able to re-use work across sites, projects, or clients. It also enables standadized dashboards to be built (programatically!) that will just work. This is likely the reason Google created their standard event names...to make it easier to deliver standard reports. We're just emulating them to make our lives easier.
  ## Saving brain power for hard problems
  Naming things is an often overlooked but vital activity in analytics implementations. Oddly or inconsistently named events can cause headaches for analysts and decision makers, but coming up with easily understood names can drain time away that could be used on actual implementations or analysis or business decision making. Standardizing event and parameter names saves time and enables focus to be place on value add activities.
</details>

<details>
  <summary>How did you decide on these standards?</summary>
  
  ## Starting Point
  We did a deep dive into Google's [automatically-collected events](https://support.google.com/analytics/answer/9234069?hl=en&ref_topic=9756175#), [enhanced measurement events](https://support.google.com/analytics/answer/9216061?hl=en&ref_topic=9756175), and [Measurement Protocol events](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events) to determine the naming standards they used. This is why we decided on snake_case for events and parameters and present tense for events as these are almost universally consistent within Google's predefined events.

  ## Debates
  ### subject_verb or verb_subject
  The `subject_verb` decision took a lot of discussion as it is inconsistent across Google's events. For instance, all of the predefined Google video and tutorial events are subject_verb (`video_start`, `tutorial_begin`), but many of the ecommerce events are verb_subject (`view_item`, `add_to_cart`, `join_group`, `generate_lead`).

  Our initial attempt to find consistency in this was thinking that maybe the verb should come first if the user is doing something, but the noun should come first if the site is doing it. That worked for many events, but not all of them. It was also a strange expectation to put on an architect to think in this way, so we changed our approach.

  In the end, we decided on `subject_verb` primarily because it's easier to visually and programmatically cluster similarly-named events when they start with the same base in many tools (GTM, BigQuery, etc) through simple alphabetizing. It's easier to at-a-glance see all the form-related events together than have to dig through data to figure out if the implementer chose `start_form` or `begin_form`.

  ### x_start vs x_begin
  Google uses `start` and `begin` as verbs on different events seemingly interchangably. 
  
  Starts:
  1. `level_start`
  2. `session_start`
  3. `video_start`

  
  Begins:
  1. `tutorial_begin`
  2. `begin_checkout`

  There wasn't much debate or strong opinions on this, so in the end we went with the one that shops up most often in Google's events. 3 > 2, so we went with start.
  ### 

</details>


<details>
  <summary>What are the limits for GA4 properties?</summary>

  Check [here](https://support.google.com/analytics/answer/11202874) for the most up-to-date info on limits.  
</details>

<details>
  <summary>Why aren't all of the parameters namespaced/prefixed?</summary>
  <p>
    Given the restrictions on how many Custom Dimensions (CDs) can be created (see FAQ above), there is a real concern (especially on non-360 accounts) that companies will run out of them and will not be able to report on everything they need to within the GA4 UI. As such, we have chosen to go with generic parameter names as often as we can. If you or your client are not all that concerned about running out of CD slots, then feel free to prefix every parameter. For instance, use form_id instead of identifier on form_view and similar form events.
  </p>  
</details>