# Send Health Worker Alert Workflow

The send alert workflow allows the infrastructure services to register alerts with an alert service. The alert service allows alert consumers to query for these alerts and send them out to health workers in whatever format is appropriate \(SMS, email, etc\).

An alert is intended as a largely one way communication to a health worker. Use cases for alerts include:

1. **Crisis Response** In response to a crisis or emergency situation, such as the 2014 and 2015 outbreaks of Ebola in western Africa, it is critical to communicate to health workers within a particular health care network and to verify, to the extent possible, the receipt of such an alert.
2. **Care Reminders** A subject of care may receive care from multiple providers across multiple health care networks, and coordination of care across providers and networks is difficult. If an Electronic Medical Record or Longitudinal/Shared Health Record is present, Care Reminder alerts can be triggered through the examination of clinical records about the subject of care. Care Reminder alerts are sent either to the subject of care or a designated health worker.

Though the infrastructure of the alerting workflow indicated below would permit communication of many types of additional messages, alerts, or notifications, it is not intended that these messages exceed the above use cases. In particular, these do not include "Critical Findings" or other types of alerts which require immediate action by a health worker.

The IHE mACM standard on which this workflow expects that additional IHE profiles utilizing mACM would be developed to address broader alerting workflows.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh3.googleusercontent.com/5pqeaiKmzar1ArIa8oQG4D_pt1AUs6-4_d5KLJXFLpkp1PdN4eYtUD5YcMO0YNTHEH4OkUp5Jom_Gy56jgz-2o5kGTV9QtIBtg79TYH2wWecLI6PzT4uXwuBlbBKPagbDw"
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
        <p>PIX/PDQ request / PIX/PDQ response</p>
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
        <p>Examples include:</p>
        <ul>
          <li>A Health Management Information System (HMIS) notices that a threshold
            indicator on the number of cases of cholera for a district. An HMIS could
            act as an Alert Reporter by querying a health worker registry to determine
            a list of all Nurses in a district and generate an alert indicating that
            they should be advised of the increased number of cholera cases.</li>
          <li>A Ministry of Health employee wishes to notify health workers of a delay
            in payment. The employee interacting with a Human Resource Information
            System (HRIS) could act as an Alert Reporter by initiating an alert to
            all formal sector paid employees to indicate that there will be a delay.</li>
          <li>A Mediator in the Interoperability Layer could monitor a Shared Health
            Record and notice that a child has missed a vaccination according to an
            established protocol of care. The Mediator would act as an Alert Reporter
            and issue an SMS reminder to send to the mother or other designated guardian.
            In the case when a mother does not have access to a cell-phone or other
            electronic device, an alert should be generated and sent to the child&#x2019;s
            caregiver. This caregiver could be a Community Health Worker, a village
            elder, or a sub-village chairman.</li>
          <li>A Mediator can monitor a central Electronic Referral System and a Shared
            Health Record to detect if the patient has missed their referral by checking
            if an encounter has been received at the Longitudinal Health Record within
            the time frame indicated in the referral. If an encounter has not been
            received the Mediator acts as an Alert Reporter and sends out an alert
            of the missed appointment to inform the health worker that originally interfaced
            with that client.</li>
        </ul>
        <p><b>Alert Aggregator -</b> A system responsible for distributing an alert
          to a health worker. The alert aggregator manages these alerts according
          to the required jurisdiction defined business context, for example dispatching
          them onto a communications platform for delivery to an intended recipient.
          <br
          />The Alert Aggregator may optionally collect statistics related to the
          dissemination of the alert such as delivery status or the value of an SMS
          response or acknowledgment.</p>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description**

![](https://lh6.googleusercontent.com/e0xjbYWnS8rwioyp6RtTf7ZtmkYEIcDO7KaKpNhr4z4yf2ALVfhqKLoLue6B1BIXrYgadaCo6pskr8_XMF_qYLod0aiuRXrWaDZ6enLwebR6y3KxfstpyG5ggvFjsP1Urw)

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
      <td style="text-align:left">Search for provider, organization, and/or facility identifier(s)</td>
      <td
      style="text-align:left">Alert Report constructs query according to business rules under which
        alert was initiated. FHIR transactions are more aligned with the mACM ITI-84
        transaction which has references to Organization, Location (e.g., facility),
        or Provider resources.</td>
        <td style="text-align:left">
          <p>FHIR DSTU2 search on Location, Provider or Patient resources OR</p>
          <p>ITI-73 Find Matching Services CSD Request
            <br />
            <br />
          </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Search for provider, organization and/or facility identifier(s)</td>
      <td
      style="text-align:left"></td>
        <td style="text-align:left">
          <p>FHIR DSTU2 search on Location, Provider or Patient resources</p>
          <p>OR</p>
          <p>ITI-73 Find Matching Services CSD Request</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">4,5</td>
      <td style="text-align:left">Return identifiers</td>
      <td style="text-align:left">FHIR transactions are more aligned with the mACM ITI-84 transaction which
        has references to Organization, Location (e.g., facility) or Provider resources</td>
      <td
      style="text-align:left">
        <p>FHIR DSTU2 bundle search response</p>
        <p>OR</p>
        <p>ITI-73 Find Matching Services response</p>
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
      <td style="text-align:left">7,8,9</td>
      <td style="text-align:left">Report Alert</td>
      <td style="text-align:left">Mobile Report Alert ITI-84 (mACM)</td>
      <td style="text-align:left">Mobile Report Alert ITI-84 (mACM)</td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Disseminate Alert</td>
      <td style="text-align:left">Disseminate alert(s) via appropriate communication mechanisms available
        to the HIE (SMS, email, POC system, etc). Transactions depend on the communication
        channel.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">11,12</td>
      <td style="text-align:left">Update dissemination status</td>
      <td style="text-align:left">
        <p>Transactions are not specified (currently) by mACM standard.</p>
        <p><b>Note:</b> RapidPro uses custom FHIR compliant endpoint &quot;Communication/$response&quot;
          and &quot;Communication/$sent&quot; for this. We can submit a Change Proposal
          to standardize this</p>
      </td>
      <td style="text-align:left"></td>
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
      <td style="text-align:left">Request for Alert Status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Query for Alert Status ITI-85 (mACM) Response</td>
    </tr>
    <tr>
      <td style="text-align:left">16</td>
      <td style="text-align:left">Request for Alert Status</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Query for Alert Status ITI-85 (mACM) Response</td>
    </tr>
  </tbody>
</table>

