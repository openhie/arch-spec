# Save Patient-level Clinical Data Workflow

This transaction allows a point of service \(PoS\) system to save patient-level clinical data to the SHR. The transaction is verified and validated against the other registries before it is saved in the SHR. The following sequence diagram shows the steps involved.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/Vp6XBRGu-U_Dmd5EKNpCZvEEum0CxOcHOj9NgHh8UMMNLMlXHmLcUE_YWueDRr4uqWLzpPfzSBLJ2k33XQIelLypjQ4wyrD17-t33GtLa8fFxW9AYDvXhiJmBl4VaLgKDg"
          alt/>
        </p>
        <p> <b>Mature</b>
        </p>
      </th>
      <th style="text-align:left">
        <ul>
          <li><b>One or more OpenHIE implementations of this workflow exist in one or more countries</b>
          </li>
          <li><b>Workflow is defined and ARB approved</b>
          </li>
          <li><b>Workflow is supported by mature standards*</b>
          </li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <ul>
          <li>XDS.b with the on-demand document (ODD) option - provide and register
            document - <a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2b.pdf">ITI-41</a>
          </li>
          <li>CDA documents profiled by IHE PCC as the clinical data</li>
          <li><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_CSD.pdf">CSD</a> -
            Find matching services - ITI-73</li>
          <li><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">PIX Query - ITI-9</a>
          </li>
          <li><b>Optionally</b>, the MHD (FHIR-based) profile may be used instead of
            the XDS.b profile to enable PoC systems to save clinical content using
            a simpler and more modern approach. This option may be supported in two
            ways:
            <ul>
              <li>The SHR itself may support the required MHD transactions.</li>
              <li>The IL can provide an adapter to convert incoming MHD transactions to
                XDS.b transactions for the SHR to process as normal.</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <ul>
          <li>The PoS system has a curated list of Providers that interact with that
            system, with knowledge of at least the providers that are relevant to that
            PoS system.</li>
          <li>The PoS system has a curated list of Facilities that this system serves,
            with knowledge of at least one member (itself).</li>
          <li>The PoS system must ensure the patient they are submitting clinical information
            about already exists. It can do this by <a href="https://docs.google.com/document/d/1vn46_f0nKDSwiSNfU1JzCat0sFvHe8y3mM5Py2nz4uU/edit#heading=h.9okp72j04n56">querying for the patient</a> and
            if they don&apos;t exist they should register them (<a href="https://docs.google.com/document/d/1vn46_f0nKDSwiSNfU1JzCat0sFvHe8y3mM5Py2nz4uU/edit#heading=h.oxo6xt910el3">Create patient demographic record workflow</a>).</li>
          <li>The PoS system is a trusted application known by the HIE and it is registered
            with the interoperability layer to be able to send and receive data securely
            (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</li>
          <li>The conditions for the validation of facility, provider and services are
            configurable to enable them to be more or less strict.</li>
          <li>All XDS submissions to the IL MUST contain author information. Either
            authorPerson or authorInstitution or both MUST be supplied. When supplying
            these, they MUST be supplied in full XCN/XON format and these MUST include
            an identifier component. This requirement is more restrictive than the
            XDS.b profile, however it is required in order to perform validation of
            the health worker and facility submitting this information.</li>
          <li>The SHR MUST be able to store certain sections of a CDA document as discrete
            data in its internal data model for use when generating on-demand documents.
            The sections that are to be supported for discrete import are those defined
            in the <a href="http://wiki.ihe.net/index.php?title=Medical_Summaries_Profile">XDS-MS specification</a>,
            as well as (optionally) any other section that is deemed useful within
            the environment in which the SHR is deployed.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <ul>
          <li>PoS - The point of service system that captures a patient clinical encounter,
            it is responsible for sending this encounter on to the HIE.</li>
          <li>IL - Mediates the transactions between the PoS system and the infrastructure
            services to facilitate easier interoperability.</li>
          <li>CR - The source of truth for patient demographic and identifier detail.
            It is able to be queried using an identifier to find the enterprise identifier
            for a particular person.</li>
          <li>IL (Interlinked Registry) - The source of truth for facility information.
            It is able to be queried for details about a particular facility by ID.
            In implementations, the FR and/or the HWR can be used if the IL is not
            required for linking health workers and facilities.</li>
          <li>SHR - Stored patients clinical information. It is able to receive and
            store a patient clinical documents.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description**

The following is a description of the interaction steps.

![](https://lh6.googleusercontent.com/cgINyEZcAplJKeT--vaOp40laQLY-LzCgtix1dVB4eBywuFJ91yS1DKZsialL9T0FeNd2d7mdErm1A4e8RfD2Y1m8_9ilmWNP-7taLl8xnw1wNfIH_U0pFQecP4SaJgH0g)

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>#</b>
      </th>
      <th style="text-align:left">Interaction</th>
      <th style="text-align:left">Data</th>
      <th style="text-align:left">Transaction Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Submit clinical encounter</td>
      <td style="text-align:left">
        <p><a href="http://wiki.ihe.net/index.php?title=Profiles#IHE_Patient_Care_Coordination_Profiles">CDA document conforming to a particular PCC profile</a>
        </p>
        <p>XDS.b provide and register document (ITI-41 from the <a href="http://www.ihe.net/Technical_Frameworks/#IT">ITI framework</a>)
          - SOAP web service</p>
        <p>and optionally</p>
        <p>MHD provide document bundle (ITI-65) - RESTful FHIR interface</p>
      </td>
      <td style="text-align:left">
        <p>XDS: <a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3MHD: <a href="http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_MHD.pdf">MHD profile supplement</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Resolve client identifier</td>
      <td style="text-align:left">HL7 QBP^Q23 message</td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>PIX Query (ITI-9)</p>
        <p>Vol. 1 - Section 5</p>
        <p>Vol. 2 - Sections 3.9</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Return person record</td>
      <td style="text-align:left">HL7 RSP^K23 message</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Extract ECID and enrich message with ECID if patient exists, else error</td>
      <td
      style="text-align:left"></td>
        <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">Fetch provider details and perform validation</td>
      <td style="text-align:left">Function urn=&apos;urn:ihe:iti:csd:2014:stored-function:provider-search&apos;</td>
      <td
      style="text-align:left"><a href="http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_CSD.pdf">IHE ITI CSD Supplement</a>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Return cached details and validation results</td>
      <td style="text-align:left">Return validation results</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Fetch facility details and perform validation</td>
      <td style="text-align:left">Function urn=&apos;urn:ihe:iti:csd:2014:stored-function:facility-search&apos;</td>
      <td
      style="text-align:left"><a href="http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_CSD.pdf">IHE ITI CSD Supplement</a>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Return cached details and validation results</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">Read validation result and enrich document with EPID and ELID</td>
      <td
      style="text-align:left"></td>
        <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Save clinical encounter</td>
      <td style="text-align:left">
        <p><a href="http://wiki.ihe.net/index.php?title=Profiles#IHE_Patient_Care_Coordination_Profiles">CDA document conforming to a particular PCC profile</a>
        </p>
        <p>XDS.b provide and register document (ITI-41 from the <a href="http://www.ihe.net/Technical_Frameworks/#IT">ITI framework</a>)
          - SOAP web service</p>
        <p>and optionally</p>
        <p>MHD provide document bundle (ITI-65) - RESTful FHIR interface
          <br />
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3 MHD: <a href="http://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_MHD.pdf">MHD profile supplement</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">Parse and store certain sections of clinical document discretely</td>
      <td
      style="text-align:left"></td>
        <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Register a CCD on-demand document for this patient</td>
      <td style="text-align:left">Generated metadata</td>
      <td style="text-align:left">
        <p><a href="http://www.ihe.net/Technical_Frameworks/#IT">IHE IT Infrastructure</a>
        </p>
        <p>Vol. 1 - Section 10, Appendix E, J, K</p>
        <p>Vol. 2a - Sections 3.18</p>
        <p>Vol. 2b - Sections 3.41, 3.42, 3.43</p>
        <p>Vol. 2x - Appendix A, B, K, L, M, N, V, W</p>
        <p>Vol. 3 - Section 4.1, 4.2, 4.3</p>
        <p><a href="http://wiki.ihe.net/index.php?title=Medical_Summaries_Profile">XDS-MS specification</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">13</td>
      <td style="text-align:left">Acknowledge encounter saved</td>
      <td style="text-align:left">
        <p>ITI-41 SOAP response</p>
        <p>and optionally</p>
        <p>ITI-65 RESTful response</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">14</td>
      <td style="text-align:left">Acknowledge encounter saved</td>
      <td style="text-align:left">
        <p>ITI-41 SOAP response</p>
        <p>and optionally</p>
        <p>ITI-65 RESTful response</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

