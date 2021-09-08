# Send Client Alert Workflow

The send alert workflow allows the infrastructure services to register alerts with an alert service. The alert service allows alert consumers to query for these alerts and send them out to clients \(patients\) in whatever format is appropriate \(SMS, email, etc\).

An alert is intended as a largely one way communication to a client of the system. Use cases for alerts include:

1. **Crisis Response** In response to a crisis or emergency situation, such as the 2014 and 2015 outbreaks of Ebola in western Africa, it is critical to communicate to clients within a particular health care network and to verify, to the extent possible, the receipt of the alert.
2. **Care Reminders** A subject of care may receive care from multiple providers across multiple health care networks, and coordination of care across providers and networks is difficult. If an Electronic Medical Record or Longitudinal/Shared Health Record is present, Care Reminder alerts can be triggered through the examination of clinical records about the subject of care. Care Reminder alerts are sent either to the subject of care.

Though the infrastructure of the alerting workflow indicated below would permit communication of many types of additional messages, alerts, or notifications, it is not intended that these messages exceed the above use cases. In particular, these do not include "Critical Findings" or other types of alerts which require immediate action.

The IHE mACM standard on which this workflow expects that additional IHE profiles utilizing mACM would be developed to address broader alerting workflows.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/SwTBO_8vzVctmDOSo5tkBN_fHnAOXCPRte9_AMicZau9PrNtdFvIjxTI4wvWx3qVdAT0IcSVeuRmdP2A89o70-CDD-L6gpWzWM2D6GjuGnLk43EDwJDsw-Cv-mjo1CioMw"
          alt/>
        </p>
        <p> <b>Maturing</b>
        </p>
      </th>
      <th style="text-align:left">
        <ul>
          <li>Workflow is defined and ARB Approved</li>
          <li>Workflow is supported by emerging IHE mACM standard in Trial Implementation</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>1. FHIR DSTU2 search on Location, Provider or Patient resources / FHIR
          DSTU2 bundle search response</p>
        <p> <b>OR</b>
        </p>
        <p>ITI-73 Find Matching Services CSD Request / ITI-73 Find Matching Services
          response</p>
        <p>2. FHIR search on Patient resources (PDQm) request / FHIR DSTU2 bundle
          search response</p>
        <p> <b>OR</b>
        </p>
        <p>PIX/PDQ request / PIX/PDQ response
          <br />
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><b>Alert Reporter -</b> The point-of-service system that captures patient
          identifiers, is responsible for sending the identifiers to the HIE.
          <br
          />An Alert Reporter shall originate or relay alerts (an alarm, either physiological
          or technical, or an advisory) to the Alert Aggregator.
          <br />This actor can optionally query an Alert Aggregator Actor for statistics
          related to the dissemination of this alert to the intended recipient(s)</p>
        <p>In the workflow below, the Alert Report is presented as a generic actor.
          Examples include:</p>
        <ul>
          <li>A Health Management Information System (HMIS) notices that a threshold
            indicator on the number of cases of cholera for a district. An HMIS could
            act as an Alert Reporter by querying a health worker registry to determine
            a list of all clients in the district and generate an alert indicating
            that they should be advised of the increased number of cholera cases and
            provide information about disease prevention.</li>
          <li>A mediator in the Interoperability Layer could monitor a Shared Health
            Record and notice that a child has missed a vaccination according to an
            established protocol of care. The Mediator would act as an Alert Reporter
            and issues an SMS reminder to send to the mother or other designated guardian.</li>
          <li>A Mediator can monitor a central Electronic Referral System and a Shared
            Health Record to detect if the patient has missed their referral by checking
            if an encounter has been received at the Longitudinal Health Record within
            the time frame indicated in the referral. If an encounter has not been
            received the Mediator acts as an Alert Reporter and sends out an out an
            alert of the missed appointment to the client.</li>
        </ul>
        <p><b>Alert Aggregator -</b> A system responsible for distributing an alert
          to a client. The alert aggregator manage these alerts according to the
          required jurisdiction defined business context, for example dispatching
          them onto a communications platform for delivery to an intended recipient.
          <br
          />The Alert Aggregator may optionally collect statistics related to the
          dissemination of the alert such as delivery status or the value of an SMS
          response or acknowledgment.</p>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description

![](https://lh3.googleusercontent.com/K-clrcMhTENXAMc6Z0SLfUJ6eJet27jz2Q8VTe5kwHhkLt_zl3GWHjMQrFMtVjZCNLBrsQSin36zkmND3nwT5Boj5udj2EzO9SJdu66orDBVT2i3wxUF7-XnRadAI3lwxg)

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left"><b>Interaction</b>
      </th>
      <th style="text-align:left"><b>Data / Notes</b>
      </th>
      <th style="text-align:left"><b>Transaction Options</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Notice an alert condition (Defined by business rules of Alert Reporter)</td>
      <td
      style="text-align:left"></td>
        <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Search for patient identifier(s)</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>FHIR search on Patient resources (PDQm) request</p>
        <p>OR</p>
        <p>PIX/PDQ request</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Search for patient identifier(s)</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">4/5</td>
      <td style="text-align:left">Return identifiers</td>
      <td style="text-align:left">FHIR transactions are more aligned with the mACM ITI-84 transaction which
        has references to Organization, Location (e.g., facility) or Provider resources</td>
      <td
      style="text-align:left">
        <p>FHIR DSTU2 bundle search response</p>
        <p>OR</p>
        <p>PIX/PDQ response</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Report Alert</td>
      <td style="text-align:left">
        <p>Identifiers of recipients passed either by reference to appropriate FHIR
          resource (requires FHIR server for those resources)</p>
        <p>OR</p>
        <p>Identifiers of recipients passed as embedded reference to appropriate
          FHIR resources (does not require FHIR server)</p>
      </td>
      <td style="text-align:left">Mobile Report Alert ITI-84 (mACM)</td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Report Alert</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Mobile Report Alert ITI-84 (mACM)</td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Search for patient identifier(s)</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>FHIR search on Patient resources (PDQm) request</p>
        <p>OR</p>
        <p>PIX/PDQ request</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">Return identifiers</td>
      <td style="text-align:left">
        <p>Current reference implementation of ILR (OpenInfoMan) supports both of
          these transactions.</p>
        <p>FHIR transactions are more aligned with the mACM ITI-84 transaction which
          has references to Organization, Location (e.g., facility) or Provider resources</p>
      </td>
      <td style="text-align:left">
        <p>FHIR DSTU2 bundle search response</p>
        <p>OR</p>
        <p>PIX/PDQ response</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Disseminate Alert</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Disseminate alert(s) via appropriate communication mechanisms available
        to the HIE (SMS, email, POC system, etc). Transactions depend on the communication
        channel.</td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">Response</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Update dissemination status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>Transactions are not specified (currently) by mACM standard.</p>
        <p>Note: RapidPro uses custom FHIR compliant endpoint &quot;Communication/$response&quot;
          and &quot;Communication/$sent&quot; for this.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">13</td>
      <td style="text-align:left">Request for Alert Status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Query for Alert Status ITI-85 (mACM) Request</td>
    </tr>
    <tr>
      <td style="text-align:left">14</td>
      <td style="text-align:left">Request for Alert Status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Query for Alert Status ITI-85 (mACM) Request</td>
    </tr>
    <tr>
      <td style="text-align:left">15</td>
      <td style="text-align:left">Request Alert Status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Query for Alert Status ITI-85 (mACM) Response</td>
    </tr>
    <tr>
      <td style="text-align:left">16</td>
      <td style="text-align:left">Request Alert Status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Query for Alert Status ITI-85 (mACM) Response</td>
    </tr>
  </tbody>
</table>

