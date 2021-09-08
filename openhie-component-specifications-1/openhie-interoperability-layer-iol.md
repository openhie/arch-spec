# OpenHIE Interoperability Layer  \(IOL\)

While the roles of other OHIE components that provide services may be more easily understood, it is the IOL that secures and orchestrates the exchange of information. Similar to an orchestra conductor, the IOL provides the central force that enables all of the HIE components to work together and interact with Point-of-Service systems outside the HIE.

See also [Non-Functional Requirements](non-functional-requirements.md).

## **OpenHIE IOL Workflow Requirements**

To be OHIE IOL component, the IOL application must be able to support the following required standard:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>#</b>
      </th>
      <th style="text-align:left"><b>IHE Standard</b>
      </th>
      <th style="text-align:left"><b>Recommendation / Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>IOLWF-1</b>
      </td>
      <td style="text-align:left">
        <p><a href="https://wiki.ihe.net/index.php/Audit_Trail_and_Node_Authentication">IHE ATNA</a> -
          this is split into two logical parts</p>
        <ul>
          <li>AT (Audit Trail) - Which describes how audit messages can be sent and
            stored in a central repository which in this case would be the IOL</li>
          <li>NA (Node Authentication) - Which describes how the IOL can authenticate
            clients (external systems) that want to send request into the exchange</li>
        </ul>
      </td>
      <td style="text-align:left">Required</td>
    </tr>
  </tbody>
</table>

In addition to this, the Interoperability layer is architected to be the single point of entry into an HIE. This means that the IOL should be involved in every OpenHIE workflow. It transparently handles transaction routing, security and auditing as these are common functions that are necessary in all workflows.

## **OpenHIE IOL Functional Requirements**

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left"><b>IOL Functional Requirements</b>
      </th>
      <th style="text-align:left"><b>Recommendation/ Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>IOLF-1</b>
      </td>
      <td style="text-align:left">The system should provide a central point of access for the services of
        the HIE. For example, this interface will provide access to the CR, PR,
        FR and SHR. This central point of access simplifies security management
        and provides a single entry point into the HIE.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-2</b>
      </td>
      <td style="text-align:left">The system shall provide routing functions that allow messages to be routed
        to the correct service provider systems within the HIE.</td>
      <td style="text-align:left">
        <br />Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-3</b>
      </td>
      <td style="text-align:left">The system shall provide a central logging mechanism for the messages
        sent through the exchange. This function should log copies of the messages
        that travel through the interoperability layer for audit and reporting
        purposes.</td>
      <td style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-4</b>
      </td>
      <td style="text-align:left">The system should allow for the rerunning of failed transactions at a
        central level, alleviating the need for Point-of-Service systems to resend
        data, for example, in the event of a problem with an infrastructure component.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-5</b>
      </td>
      <td style="text-align:left">Should support transformation of messages that travel from the interoperability
        layer to service provider systems and vice versa if the service provider
        is not able to communicate in the required format, i.e. provides implementation
        specific adapters to transform messages from the interoperability layer&#x2019;s
        internal form to a form that the service provider expects (e.g., SHR, CR,
        PR).</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-6</b>
      </td>
      <td style="text-align:left">
        <p>The system should allow for the routing of messages to the appropriate
          architecture component or external Point-of-Service system.</p>
        <ul>
          <li>Performs orchestration tasks for complex transactions to take the burden
            off client systems. This orchestration may contact multiple service providers
            within the HIE on a client&#x2019;s behalf and compile an appropriate response
            to return to the client.</li>
          <li>Examples of orchestration could be the execution of a care plan or the
            validation of elements (such as identifiers or codes) in a message against
            other service providers within the HIE (e.g., PR, CR, FR, TS).</li>
          <li>Orchestration tasks are those that are required to complete the current
            transaction and therefore must be executed timeously as the transaction
            cannot continue without these steps.</li>
        </ul>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-7</b>
      </td>
      <td style="text-align:left">
        <p>The systems shall include an interface into which a workflow engine can
          be connected.</p>
        <ul>
          <li>This workflow engine should be able to keep track of the long running
            state of a patient&apos;s care and would be able to perform actions based
            on this context (such as sending alerts) to improve patient care.</li>
          <li>This workflow engine is out of scope for an Interoperability Layer. However,
            the Interoperability Layer is expected to expose an interface to allow
            this sort of systems to be implemented.</li>
        </ul>
      </td>
      <td style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-8</b>
      </td>
      <td style="text-align:left">The system should support the ability to be extended by allowing additional
        mediation functions to be added or removed as they are needed.</td>
      <td
      style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-9</b>
      </td>
      <td style="text-align:left">The system shall support a mechanism for error management and tracking,
        e.g. a console for viewing failed transactions.</td>
      <td style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-10</b>
      </td>
      <td style="text-align:left">The system shall allow for failed transactions to be grouped by error
        type and reason so that errors can be rectified efficiently by finding
        the root cause of the error, fixing the problem, and re-running those transactions.</td>
      <td
      style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-11</b>
      </td>
      <td style="text-align:left">The system should support the ability for a user to re-run errored transactions
        through the HIE once the reason for their failure has been rectified.</td>
      <td
      style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-12</b>
      </td>
      <td style="text-align:left">The system shall provide authorized users with a view of metrics for monitoring
        the flow of messages through the HIE.</td>
      <td style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-13</b>
      </td>
      <td style="text-align:left">The system shall manage the security of the HIE through authentication
        (identity verification), authorization (permission to interact with specified
        HIE components) and encryption and decryption of messages.</td>
      <td style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-14</b>
      </td>
      <td style="text-align:left">The system shall support Authentication and Authorization of systems trying
        to send data to the HIE.</td>
      <td style="text-align:left">Requirement</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-15</b>
      </td>
      <td style="text-align:left">The system should support the encryption of data in flight (when not on
        a physically secure network) and at rest (whenever data is stored, e.g.
        when transactions are stored for logging).</td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>IOLF-16</b>
      </td>
      <td style="text-align:left">The system should capture monitoring statistics, such as transaction loads
        and performance metrics, and provides a view of these for monitoring the
        flow of messages through the HIE.</td>
      <td style="text-align:left">Recommendation</td>
    </tr>
  </tbody>
</table>

