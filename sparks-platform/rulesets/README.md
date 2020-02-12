# Rulesets

A ruleset represents a single “knowledge base” and the rules contained inside of it. Generally, a ruleset applies to a specific problem or domain.

The Sparks Platform Rule services are built atop the Drools engine. Drools is a battle-tested inference engine whose basic function is to “match data to business rules and determine whether and how to execute rules.”

For a good explanation of inferencing and truth maintenance using Drools see [this link](https://docs.jboss.org/drools/release/latest/drools-docs/html_single/index.html#inference-and-truth-maintenance_decision-engine).

Rules are great when the logic changes often and/or domain experts \(business analysts\) are on-hand to manage the rules.

### Use Cases

Some use cases where the Sparks Platform has been or is being used now are:

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">&lt;b&gt;&lt;/b&gt;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>Government</b>
        </p>
        <p>- Tax calculations</p>
        <p>- Fee calculations</p>
        <p>- Application processing</p>
      </td>
      <td style="text-align:left">
        <p><b>Manufacturing</b>
        </p>
        <p>- Supply chain management</p>
        <p>- Product configuration</p>
        <p>- Simulations</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Insurance</b>
        </p>
        <p>- Rating and categorization</p>
        <p>- Automated underwriting</p>
        <p>- Compliance</p>
      </td>
      <td style="text-align:left">
        <p><b>Financial Services</b>
        </p>
        <p>- Loan origination</p>
        <p>- Asset management</p>
        <p>- Document automation</p>
      </td>
    </tr>
  </tbody>
</table>