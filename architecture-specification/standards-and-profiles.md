# Standards and Profiles

## IHE Profiles

The following are the [IHE](http://www.ihe.net/) [profiles](http://wiki.ihe.net/index.php?title=Profiles#IHE_IT_Infrastructure_Profiles) that OpenHIE is working toward demonstrating or has demonstrated as supported in reference implementations.  However, the OpenHIE architecture is **not limited to supporting these profiles**.  

<table>
  <thead>
    <tr>
      <th style="text-align:left">Standard</th>
      <th style="text-align:left">Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Aggregate_Data_Exchange">ADX</a>
      </td>
      <td style="text-align:left">The <b>Aggregate Data Exchange (ADX)</b> Profile enables interoperable public
        health reporting of aggregate health data. ADX will typically be used to
        represent routinely reported aggregate data such as the numerators and
        denominators which can be used in the construction of public health indicators.
        Refer to the <a href="../introduction/aggregate-reporting-workflows/">Aggregate Reporting Workflows</a> for
        more information on how this is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://github.com/IHE/QRPH.ADX.COVID19">ADX-COVID</a>
      </td>
      <td style="text-align:left">The ADX (<b>Aggregate Data Exchange)</b> profile affords data exchange
        partners a way to define a Data Structure Definition and the associated
        normative schema of the data message for a particular indicator report.
        Refer to the <a href="../introduction/aggregate-reporting-workflows/">Aggregate Reporting Workflows</a> for
        more information on how this is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://wiki.ihe.net/index.php/Aggregate_Data_Exchange_-_HIV">ADX-HIV</a>
      </td>
      <td style="text-align:left">The ADX (<b>Aggregate Data Exchange)</b> profile affords data exchange
        partners a way to define a Data Structure Definition and the associated
        normative schema of the data message for a particular indicator report.
        To foster further adoption, the Aggregate Data Exchange-HIV (ADX-HIV) profile
        leverages the ADX profile version 2.1, which is currently published for
        trial implementation, to develop a content specification specifically for
        HIV. Refer to the <a href="../introduction/aggregate-reporting-workflows/">Aggregate Reporting Workflows</a> for
        more information on how this is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Antepartum_Care_Summary_Profile">APS</a>
      </td>
      <td style="text-align:left">The <b>APS</b> document is a medical summary and inherits all header constraints
        from Medical Summaries.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Audit_Trail_and_Node_Authentication">ATNA</a>
      </td>
      <td style="text-align:left">The <b>Audit Trail and Node Authentication (ATNA)</b> Integration Profile
        establishes security measures which, together with the Security Policy
        and Procedures, provide patient information confidentiality, data integrity
        and user accountability</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="ftp://ftp.ihe.net/DocumentPublication/CurrentPublished/ITInfrastructure/IHE_ITI_Suppl_CSD.pdf">CSD</a>
      </td>
      <td style="text-align:left">The <b>Care Services Discovery (CSD)</b> Profile supports queries across
        related directories containing data about: organizations, facilities, services
        and providers. Queries against an optional &#x201C;FreeBusy&#x201D; service
        are also supported; this FreeBusy information would support the development
        of a list of schedulable time slots for providers or services at specific
        facilities. Refer to the <a href="../introduction/care-services-discovery/">Care Services Discovery</a> workflows
        for more information on how this is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Consistent_Time">CT</a>
      </td>
      <td style="text-align:left"><b>Consistent Time (CT)</b> enables system clocks and time stamps of computers
        in a network to be synchronized (median error less than 1 second).</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Mobile_Alert_Communication_Management(mACM)">mACM</a>
      </td>
      <td style="text-align:left"><b>Mobile Alert Communication Management</b> Sending one-way alerts to
        health workers and health system beneficiaries (clients). See the <a href="../introduction/alerting-sending-reminders-or-information/">Alerting / Sending Reminders or Information</a> section
        of this document for more information on how it is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://wiki.ihe.net/index.php/Mobile_Aggregate_Data_Exchange_(mADX)">mADX</a>
      </td>
      <td style="text-align:left">Emerging FHIR standard for Aggregate Data Exchange. Refer to the <a href="../introduction/aggregate-reporting-workflows/">Aggregate Reporting Workflows</a> for
        more information on how this is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_mCSD.pdf">mCSD</a>
      </td>
      <td style="text-align:left"><b>Mobile Care Services Discovery</b> Profile supports queries across related
        directories containing data about: organizations, facilities, services
        and providers. Based on HL7 FHIR. Refer to the <a href="../introduction/care-services-discovery/">Care Services Discovery</a> for
        more information on how this is used.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php/Mobile_access_to_Health_Documents_(MHD)">MHD</a> 
      </td>
      <td style="text-align:left"><b>Mobile Access to Health Documents</b> profile defines a simple HTTP
        interface to an XDS like environment. The MHD profile is intended for any
        system that prefers the simplified HTTP RESTful technology rather than
        the more robust technology used in XDS. It defines transactions to a) submit
        a set of documents and metadata from the mobile device to a document receiver,
        b) find the document submission set metadata based on query parameters;
        c) find document entries containing metadata based on query parameters,
        and d) retrieve a copy of a specific document.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://wiki.ihe.net/index.php/Mobile_Health_Document_Sharing_(MHDS)">MHDS</a>
      </td>
      <td style="text-align:left">The <b>Mobile Health Document Sharing</b> profile specifies how a collection
        of IHE profiles can be used by communities for exchanging health information.
        These IHE profiles include support for patient identification, health document
        location and retrieval, provider directories, and the protection of privacy
        and security. MHDS shows how several IHE profiles work together to provide
        a standards-based, interoperable approach to community health information
        sharing.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Patient_Demographics_Query">PDQ</a>
      </td>
      <td style="text-align:left">The <b>Patient Demographics Query (PDQ)</b> Integration Profile lets applications
        query a central patient information server and retrieve a patient&#x2019;s
        demographic information.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Patient_Demographics_Query_for_Mobile_(PDQm)">PDQm</a>
      </td>
      <td style="text-align:left">The <b>Patient Demographics Query for Mobile (PDQm)</b> Profile defines
        a lightweight RESTful interface to a patient demographics supplier leveraging
        technologies readily available to mobile applications and lightweight browser
        based applications. The functionality is identical to the PDQ Profile described
        in the ITI TF-1:8.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php?title=Patient_Identifier_Cross-Referencing">PIX</a>
      </td>
      <td style="text-align:left">
        <p>The <b>Patient Identifier Cross Referencing (PIX)</b> Integration Profile
          supports the cross-referencing of patient identifiers from multiple Patient
          Identifier Domains by:</p>
        <ul>
          <li>Transmitting patient identity information from an identity source to the
            Patient Identifier Cross-reference Manager.</li>
          <li>Providing the ability to access the list(s) of cross-referenced patient
            identifiers either via a query/ response or via an update notification</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://wiki.ihe.net/index.php/Patient_Master_Identity_Registry_(PMIR)">PMIR</a>
      </td>
      <td style="text-align:left">The <b>Patient Master Identity Registry</b> (PMIR) Profile supports the
        creating, updating and deprecating of patient master identity information
        about a subject of care, as well as subscribing to changes to the patient
        master identity, using the HL7 FHIR standard resources and RESTful transactions.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://wiki.ihe.net/index.php/Sharing_Valuesets,_Codes_and_Maps_(SVCM)">SVCM</a>
      </td>
      <td style="text-align:left"><b>Shared Valuesets, Codes, and Maps</b> provides basic transactions associated
        with Terminology Services. Transactions are based on FHIR CodeSystem, ValueSet,
        and ConceptMap Resource operations. SVCM is currently in Trial Implementation
        status. See the <a href="../introduction/terminology-service-workflow/">Terminology Service Workflows</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://wiki.ihe.net/index.php/XDS.b_Implementation">XDS.b</a>
        <a
        href="http://wiki.ihe.net/index.php/XDS.b_Implementation"></a>
      </td>
      <td style="text-align:left"><b>Cross-Enterprise Document Sharing (XDS.b)</b> is focused on providing
        a standards-based specification for managing the sharing of documents between
        any healthcare enterprise, ranging from a private physician office to a
        clinic to an acute care in-patient facility and personal health record
        systems.</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
For documentation on how many of these profiles work together in an HIE, see [MHDS](https://wiki.ihe.net/index.php/Mobile_Health_Document_Sharing_%28MHDS%29), [IHE  White Paper ](https://profiles.ihe.net/ITI/HIE-Whitepaper/index.html)and the [Workflow \(Exchange\) Specification](../introduction/) section of this Specification.  
{% endhint %}



