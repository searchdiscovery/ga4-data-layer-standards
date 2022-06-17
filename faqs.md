# Frequently Asked Questions

<details>
  <summary>Are there any general naming conventions?</summary>
  
  ## Event Names
  1. Always use lowercase [snake_case](https://en.wikipedia.org/wiki/Snake_case)
  2. Event noun/subject should always come before event action/verb
  3. Event verbs should always be present tense

  Examples
  1. `form_start`, not `Form Start` or `Form_Start` or `form-start`
  2. `form_view`, not `view_form`
  3. `form_complete`, not `form_completed`

  ## Parameter names
  1. Always use lowercase [snake_case](https://en.wikipedia.org/wiki/Snake_case)
  2. Tend towards generic parameter names instead of namespaced/prefixed to save CD slots whenever possible. If there is already a parameter on another event that could be used, consider using it. See "Why aren't all of the parameters namespaced/prefixed?" below for additional details.
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