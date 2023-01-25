# WilmU SEO Documentation
<a name="top"></a>
## Table of contents

- [WilmU SEO Documentation](#wilmu-seo-documentation)
  - [Table of contents](#table-of-contents)
  - [How to generate structured data](#how-to-generate-structured-data)
  - [Use Google Tag Manager to generate JSON-LD dynamically](#use-google-tag-manager-to-generate-json-ld-dynamically)
    - [Using variables in Google Tag Manager](#using-variables-in-google-tag-manager)
      - [Create custom user-defined variables in Google Tag Manager](#create-custom-user-defined-variables-in-google-tag-manager)
  - [](#)
  - [Structured data that Google supports](#structured-data-that-google-supports)
    - [Article - Reference](#article---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters)
      - [Example Code](#example-code)
    - [Breadcrumbs - Reference](#breadcrumbs---reference)
    - [Carousel - Reference](#carousel---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-1)
      - [ Example Code](#-example-code)
    - [Course - Reference](#course---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-2)
    - [Degree/Certificates](#degreecertificates)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-3)
      - [Example Code](#example-code-1)
    - [Educational Occupational Program](#educational-occupational-program)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-4)
      - [Example Code](#example-code-2)
    - [Estimated Salary - Reference](#estimated-salary---reference)
    - [Event - Reference](#event---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-5)
      - [Example Code](#example-code-3)
    - [FAQ - Reference](#faq---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-6)
      - [Example Code](#example-code-4)
    - [How-To - Reference](#how-to---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-7)
      - [Example Code](#example-code-5)
    - [Learning Video - Reference](#learning-video---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-8)
      - [Example Code](#example-code-6)
    - [Local Business - Reference](#local-business---reference)
    - [Logo - Reference](#logo---reference)
    - [Person](#person)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-9)
      - [Example Code](#example-code-7)
    - [Q\&A - Reference](#qa---reference)
    - [Sitelinks Search box - Reference](#sitelinks-search-box---reference)
      - [Required and Recommended Parameters](#required-and-recommended-parameters-10)
      - [Example Code](#example-code-8)
    - [Speakable - Reference](#speakable---reference)
    - [Video - Reference](#video---reference)
 

## <a name="how-to-generate-structured-data"></a>How to generate structured data

There are different ways to generate structured data with JavaScript, but the most common are:

- [Google Tag Manager](https://developers.google.com/search/docs/appearance/structured-data/generate-structured-data-with-javascript#use-google-tag-manager)[^bignote]
- [Merkle Schema Markup Generator](https://technicalseo.com/tools/schema-markup-generator/)
- [editor.md](https://pandao.github.io/editor.md/en.html)
- [Dillinger](https://dillinger.io/)
- [Schemantra](https://schemantra.com/schema_list/)
- MS Visual Code

## <a name="use-google-tag-manager-to-generate-json-ld-dynamically"></a>Use Google Tag Manager to generate JSON-LD dynamically

[^bignote]: To generate structured data with Google Tag Manager, follow these steps:

  1.  [Sign in to Google Tag Manager](https://tagmanager.google.com/)
  2.  Add a new **Custom HTML** tag to the container.
  3.  Paste the desired structured data block into the tag content.
  4.  Install the container as shown in the **Install Google Tag Manager** section of your container's admin menu.
  5.  To add the tag to your website, publish your container in the Google Tag Manager interface.
  6.  [Test your implementation](https://developers.google.com/search/docs/appearance/structured-data/generate-structured-data-with-javascript#testing).

  ### <a name="using-variables-in-google-tag-manager"></a>Using variables in Google Tag Manager

Google Tag Manager (GTM) supports [variables](https://support.google.com/tagmanager/topic/7683268?ref_topic=3441647) to use information on the page as part of your structured data. 
Use variables to extract the structured data from the page instead of duplicating the information in GTM. 

| Built-in variables                                                                                     | User-defined variables                                                                                                      |
| ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| For [web containers](https://support.google.com/tagmanager/answer/7182738?hl=en&ref_topic=7182737)     | For [web](https://support.google.com/tagmanager/answer/7683362?hl=en&ref_topic=9125128)                                     |
| For [web containers](https://support.google.com/tagmanager/answer/7182738?hl=en&ref_topic=7182737)     | For [mobile](https://support.google.com/tagmanager/answer/7683157?hl=en&ref_topic=9125128)                                  |
| For [iOS containers](https://support.google.com/tagmanager/answer/7182836?hl=en&ref_topic=7182737)     | [Format values in user-defined web variables](https://support.google.com/tagmanager/answer/9121006?hl=en&ref_topic=9125128) |
| For [Android containers](https://support.google.com/tagmanager/answer/7182414?hl=en&ref_topic=7182737) |                                                                                                                             |


#### <a name="create-custom-user-defined-variables-in-google-tag-manager"></a>Create custom user-defined variables in Google Tag Manager
Create custom user-defined variables in Google Tag Manager to suit specific requirements that might not already be covered by [built-in variables](https://support.google.com/tagmanager/topic/7182737).
To create a new user-defined variable:
1.  In the left navigation, click **Variables**.
2.  In the User-Defined Variables section, click **New**.
3.  Click **Variable Configuration** and select the desired variable type. 
4.  Complete the options for the selected variable type.
5.  Name the variable. Use a naming scheme that is descriptive of the variable's function, e.g. "_Data Layer Variable - Product Name_."
6.  Click **Save**.

For example, if you create a variable called `course_name`, you can dynamically create a **Course** block that uses the page title as the course name.

```javascript
function()  {  return document.title;  }
```

You can then use `{{course_name}}` in your custom tag HTML.

**We recommend to create variables to collect all the necessary information from the page using variables.**

Here is an example for the custom HTML tag content:
Assumes that you defined the variables recipe_name, recipe_image and recipe_author in GTM.
```json

{
  "@context": "https://schema.org",
  "@type": "Course",
  "url": "http://smartcatalog.co/en/Catalogs/Wilmington-University/Current/Undergraduate-Catalog/Courses/ENG-English/100/ENG-121",

  "name": "{{course_name}}",
  "description": "{{course_desc}}",
  "provider": {
    "@type": "Organization",
    "name": "Wilmington University",
    "sameAs": "https://www.wilmu.edu"
  },
  "hasCourseInstance": {
    "@type": "CourseInstance",
    "courseMode": [
      "part-time",
      "full-time",
      "distance learning",
      "MOOC",
      "online"    
    ],
    "endDate": "2022-03-21",
    "startDate": "2023-02-15"
  }
}
```
## <a name="schema"></a>
Schema documentation for Wilmington University's SEO projects. The wiki contains examples and related schema's associated with wilmu.edu web content.

## <a name="structured-data-that-google-supports"></a>Structured data that Google supports 
**This is a partial list that contains only data that benefits Wilmington University.**

### <a name="article">Article</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/article)
#### <a name="articleparameters"></a>Required and Recommended Parameters

| Property      | Type         | Example Value                                                                                                             |
| :------------ | :----------- | :------------------------------------------------------------------------------------------------------------------------ |
|               | NewsArticle  |                                                                                                                           |
| url           | URL          | https://blog.wilmu.edu/news/2023/01/18/wilmington-university-president-dr-laverne-harmon-selected-for-prestigious-boards/ |
| publisher     | Organization |                                                                                                                           |
| name          | Text         | Wilmington University                                                                                                     |
| logo          | ImageObject  |                                                                                                                           |
| url           | URL          | https://blog.wilmu.edu/news/wp-content/uploads/sites/28/2020/01/wilmu-logo-color-350x92.png                               |
| headline      | Text         | Wilmington University President Dr. LaVerne Harmon Selected for Prestigious Boards                                        |
| image         | URL          | https://blog.wilmu.edu/news/wp-content/uploads/sites/28/2023/01/LTH-HS_22-23_1080x1080-1080x694.jpg                       |
| datePublished | Date         | 2023/01/18T3:13-05:00                                                                                                     |

#### <a name="articleexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
   "@type": "NewsArticle",
   "url": "https://blog.wilmu.edu/news/2023/01/18/wilmington-university-president-dr-laverne-harmon-selected-for-prestigious-boards/",
  "publisher": {
    "@type": "Organization",
    "name": "Wilmington University",
    "logo": {
      "@type": "ImageObject",
      "url": "https://blog.wilmu.edu/news/wp-content/uploads/sites/28/2020/01/wilmu-logo-color-350x92.png"
    }
  },
  "headline": "Wilmington University President Dr. LaVerne Harmon Selected for Prestigious Boards",
  "image":[
    "https://blog.wilmu.edu/news/wp-content/uploads/sites/28/2023/01/LTH-HS_22-23_1080x1080-1080x694.jpg"
  ],
  "datePublished":"2023/01/18T3:13-05:00"
}
```

### <a name="breadcrumbs">Breadcrumbs</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/breadcrumb)

### <a name="carousel">Carousel</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/carousel)
Rich results that display in a sequential list or gallery from a single site. This feature must be combined with one of the following features: Course. (e.g., multiple courses)

#### <a name="carouselparameters"></a>Required and Recommended Parameters

| Property        | Type                  | Example Value                                                                                                                                 |
| :-------------- | :-------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
|                 | ItemList              |                                                                                                                                               |
| itemListElement | ListItem, Text, Thing | ListItem                                                                                                                                      |
|                 | ListItem              |                                                                                                                                               |
| position        | Integer               | 1, 2, ...                                                                                                                                     |
| item            | Thing                 | Course                                                                                                                                        |
| url             | URL                   | Find course on [Smart Catalog](https://smartcatalog.co/en/Catalogs/Wilmington-University/Current/)                                            |
| name            | Text                  | English Composition I                                                                                                                         |
| description     | Text                  | This course will help students become more proficient and effective writers, while also developing reading comprehension and analysis skills. |
| provider        | Organization          |                                                                                                                                               |
| name            | Text                  | Wilmington University                                                                                                                         |
| sameAs          | URL                   | https://www.wilmu.edu                                                                                                                         |

#### <a name="carouselexample"></a> Example Code

```json
{
  "@context": "https://schema.org",
  "@type": "ItemList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "item": {
        "@type": "Course",
        "url":"http://smartcatalog.co/en/Catalogs/Wilmington-University/Current/Undergraduate-Catalog/Courses/ENG-English/100/ENG-121",
        "name": "English Composition I",
        "description": "This course will help students become more proficient and effective writers, while also developing reading comprehension and analysis skills.",
        "provider": {
          "@type": "Organization",
          "name": "Wilmington University",
          "sameAs": "https://www.wilmu.edu"
        }
      }
    },
    {
      "@type": "ListItem",
      "position": 2,
      "item": {
        "@type": "Course",
        "url":"http://smartcatalog.co/en/Catalogs/Wilmington-University/Current/Undergraduate-Catalog/Courses/ENG-English/100/ENG-122",
        "name": "English Composition II",
        "description": "This is a CS course that builds on the basics learned in the Introduction course.",
        "provider": {
          "@type": "Organization",
          "name": "Wilmington University",
          "sameAs": "https://www.wilmu.edu"
        }
      }
    }
  ]
}
```

 [Back to top](#top) 
### <a name="course">Course</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/course)
Educational courses that appear in a provider-specific list. Courses can include the course title, provider, and a short description.

 #### <a name="courseparameters"></a>Required and Recommended Parameters

| Property          | Type           | Example Value                                                                                                                                 |
| :---------------- | :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
|                   | Course         |                                                                                                                                               |
| url               | URL            | Find course on [Smart Catalog](https://smartcatalog.co/en/Catalogs/Wilmington-University/Current/)                                            |
| name              | Text           | English Composition                                                                                                                           |
| description       | Text           | This course will help students become more proficient and effective writers, while also developing reading comprehension and analysis skills. |
| provider          | Organization   |                                                                                                                                               |
| name              | Text           | Wilmington University                                                                                                                         |
| sameAs            | URL            | https://www.wilmu.edu                                                                                                                         |
| hasCourseInstance | CourseInstance |                                                                                                                                               |
| courseMode        | Text           | part-time, full-time, distance learning, MOOC, online                                                                                         |
| endDate           | Date           | 2022-03-21                                                                                                                                    |
| startDate         | Date           | 2023-02-15                                                                                                                                    |

### <a name="degree">Degree/Certificates</a>

#### <a name="degreeparameters"></a>Required and Recommended Parameters

| Property                     | Type                                         | Example Value                                                                                                      |
| :--------------------------- | :------------------------------------------- | :----------------------------------------------------------------------------------------------------------------- |
|                              | EducationalOccupationalCredential            |                                                                                                                    |
| name                         | Text                                         | Juris Doctor Degree from Wilmington University School of Law                                                       |
| description                  | Text                                         | The three-year J.D. program offered in a full-time day, in-person format from Wilmington University School of Law. |
| timeToComplete               | Duration                                     | P3Y                                                                                                                |
| educationalProgramMode       | Text, URL                                    | online, onsite or blended; synchronous or asynchronous; full-time or part-time                                     |
| numberOfCredits              | Integer, StructuredValue                     | 86                                                                                                                 |
| termDuration                 | Duration                                     | P3M                                                                                                                |
| termsPerYear                 | Number                                       | 2                                                                                                                  |
| url                          | URL                                          | https://law.wilmu.edu/academics/full-time.aspx                                                                     |
| educationalCredentialAwarded | EducationalOccupationalCredential, Text, URL | Juris Doctor                                                                                                       |
| offers                       | Demand, Offer                                |                                                                                                                    |
| category                     | CategoryCode, Text, URL                      | 3-Year Full-Time Day Program                                                                                       |
| priceSpecification           | PriceSpecification                           |                                                                                                                    |
| price                        | Number, Text                                 | 24000                                                                                                              |
| priceCurrency                | Text                                         | USD                                                                                                                |
| relevantOccupation           | Occupation                                   |                                                                                                                    |
| name                         | Text                                         | Lawyers                                                                                                            |
| occupationalCategory         | CategoryCode                                 | [Category Reference](https://www.onetcenter.org/taxonomy.html)                                                     |
| inCodeSet                    | CategoryCodeSet                              |                                                                                                                    |
| name                         | Text                                         | O*Net-SOC                                                                                                          |
| dateModified                 | Date, DateTime                               | 2022                                                                                                               |
| url                          | URL                                          | https://www.onetonline.org/                                                                                        |
| codeValue                    | Text                                         | 23-1011.00                                                                                                         |
| name                         | Text                                         | Lawyers                                                                                                            |
| url                          | URL                                          | https://www.onetonline.org/link/summary/23-1011.00                                                                 |

#### <a name="degreeexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
  "@type": "EducationalOccupationalCredential",
  "name": "Juris Doctor Degree from Wilmington University School of Law",
  "description": "he three-year J.D. program offered in a full-time day, in-person format from Wilmington University School of Law.",
  "timeToComplete": "P3Y",
  "educationalProgramMode": [
    "onsite",
    "full-time"
  ],
  "numberOfCredits": 86,
  "termDuration": "P3M",
  "termsPerYear": 2,
  "url": "https://law.wilmu.edu/academics/full-time.aspx",
  "educationalCredentialAwarded": {
    "@type": "EducationalOccupationalCredential",
    "credentialCategory": "Juris Doctor"
  },
  "offers": {
    "@type": "Offer",
    "category": "3-Year Full-Time Day Program",
    "priceSpecification": {
      "@type": "PriceSpecification",
      "price": 24000,
      "priceCurrency": "USD"
    }
  },
  "relevantOccupation": {
    "@type": "Occupation",
    "name": "Lawyers",
    "occupationalCategory": {
      "@type": "CategoryCode",
      "inCodeSet": {
        "@type": "CategoryCodeSet",
        "name": "O*Net-SOC",
        "dateModified": "2022",
        "url": "https://www.onetonline.org/"
      },
      "codeValue": "23-1011.00",
      "name": "Lawyers",
      "url": "https://www.onetonline.org/link/summary/23-1011.00"
    }
  }
}
```

### <a name="eop">Educational Occupational Program</a>

#### <a name="eopparameters"></a>Required and Recommended Parameters

| Property                     | Type                                                       | Example Value                                                    |
| :--------------------------- | :--------------------------------------------------------- | :--------------------------------------------------------------- |
|                              | EducationalOccupationalProgram                             |                                                                  |
| name                         | Text                                                       | Undergraduate Computer Science Degree from Wilmington University |
| url                          | URL                                                        | https://www.wilmu.edu/nursing/                                   |
| provider                     | CollegeOrUniversity                                        |                                                                  |
| name                         | Text                                                       | Wilmington University                                            |
| address                      | Text                                                       | PostalAddress                                                    |
| streetAddress                | Text                                                       | 320 N. DuPont Hwy                                                |
| addressLocality              | Text                                                       | New Castle                                                       |
| addressRegion                | Text                                                       | DE                                                               |
| postalCode                   | Text                                                       | 19720                                                            |
| timeToComplete               | Duration                                                   | P4Y                                                              |
| educationalCredentialAwarded | EducationalOccupationalCredential, Text, URL               | EducationalOccupationalCredential                                |
| credentialCategory           | DefinedTerm, Text, URL                                     | Bachelor of Science in Computer Science                          |
| programPrerequisites         | AlignmentObject, Course, EducationalOccupationalCredential | EducationalOccupationalCredential                                |
| credentialCategory           |                                                            |                                                                  |
| offers                       | Demand, Offer                                              | Offer                                                            |
| category                     | Text                                                       | Resident Tuition                                                 |
| priceSpecification           | PriceSpecification                                         | PriceSpecification                                               |
| price                        | Number, Text                                               | 16278                                                            |
| priceCurrency                | Text                                                       | USD                                                              |
| offers                       | Demand, Offer                                              | Offer                                                            |
| category                     | Text                                                       | International Tuition                                            |
| priceSpecification           | PriceSpecification                                         | PriceSpecification                                               |
| price                        | Number, Text                                               | 37344                                                            |
| priceCurrency                | Text                                                       | USD                                                              |

#### <a name="eopexample"></a>Example Code

```json
{
  "@context": "http://schema.org/",
  "@type": "EducationalOccupationalProgram",
  "name": "Undergraduate Computer Science Degree from College Name",
  "url": "http://www.collegename.edu/CS",
   "provider": {
    "@type": "CollegeOrUniversity",
    "name": "College Name Community College",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "320 N. DuPont Hwy",
      "addressLocality": "New Castle",
      "postalCode": "19720",
      "addressRegion": "DE",
      "addressCountry": "US"
    },
  },
  "timeToComplete": "P4Y",
  "educationalCredentialAwarded": {
    "@type": "EducationalOccupationalCredential",
    "credentialCategory": "Bachelor of Science in Computer Science"
  },
  "programPrerequisites": {
      "@type": "EducationalOccupationalCredential",
      "credentialCategory": "High school diploma"
  },
  "offers": [
    {
      "@type": "Offer",
      "category": "Resident Tuition",
      "priceSpecification": {
        "@type": "PriceSpecification",
        "price": 16278,
        "priceCurrency": "USD"
      }
    },
    {
      "@type": "Offer",
      "category": "International Tuition",
      "priceSpecification": {
        "@type": "PriceSpecification",
        "price": 37344,
        "priceCurrency": "USD"
      }
    }
  ]
}
```


### <a name="salary">Estimated Salary</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/estimated-salary)
Salary estimate information, such as salary ranges and region-based salary averages for job types, displayed in the job search experience on Google.

### <a name="event">Event</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/event)
An interactive rich result that shows a list of organized events, such as webinars or commencement, that people may attend at a particular time and place.

**All events must follow:**
  - eEvent is at a physical location **ONLY** and happens as scheduled.
  - Each event **MUST** have a unique URL.
  - Start and end dates **MUST** be added to multiple day events.
  - Note: Currently, Google only supports pages that focus on a single event. We recommend adding markup to your event posting pages instead of pages that list schedules or multiple events.

#### <a name="eventparameters"></a>Required and Recommended Parameters

| Property            | Type          | Example Value                                                                                                                                 |
| :------------------ | :------------ | :-------------------------------------------------------------------------------------------------------------------------------------------- |
|                     | Event         |                                                                                                                                               |
| name                | Text          | Adjunct Faculty Workshop                                                                                                                      |
| startDate           | Date          | 2022-09-05T9:00-05:00 (Delaware `startDate` value = GMT/UTC-5 -05:00 standard time and GMT/UTC-4 -04:00 daylight savings time)                |
| endDate             | Date          | 2022-09-06T9:00-05:00                                                                                                                         |
| description         | Text          | This course will help students become more proficient and effective writers, while also developing reading comprehension and analysis skills. |
| provider            | Organization  |                                                                                                                                               |
| name                | Text          | Wilmington University                                                                                                                         |
| sameAs              | URL           | https://www.wilmu.edu                                                                                                                         |
| presenter           | name          | Wil E Coyote                                                                                                                                  |
| place               | name          | Wilmington University New Castle                                                                                                              |
| VirtualLocation     | URL           | https://events.wilmu.edu/site/facultyandstaff/event/move-it-with-melissa--low-impact-cardio--stretch---webinar-75/                            |
| address             | PostalAddress |                                                                                                                                               |
| streetAddress       |               | 320 N. DuPont Hwy                                                                                                                             |
| addressLocality     |               | New Castle                                                                                                                                    |
| postalCode          |               | 19720                                                                                                                                         |
| addressRegion       |               | DE                                                                                                                                            |
| addressCountry      |               | US                                                                                                                                            |
| url                 | URL           | paste `https://events/wilmu.edu/{EVENTDATA}` from the events manager                                                                          |
| eventAttendanceMode | Text          | <mark>When this property is omitted, event defaults to OfflineEventAttendanceMode meaning a physical location.</mark>                         |

#### <a name="eventexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "Adjunct Faculty Workshop",
  "url" : "https://www.wilmu.edu/...",
  "startDate": "2022-09-05T9:00-05:00",
  "endDate": "2022-09-06T09:00-05:00",
  "eventAttendanceMode": "https://schema.org/OfflineEventAttendanceMode",
  "eventStatus": "https://schema.org/EventScheduled",
  "location": [{
    "@type": "Place",
    "name": "Wilmington University New Castle",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "320 N. DuPont Hwy",
      "addressLocality": "New Castle",
      "postalCode": "19720",
      "addressRegion": "DE",
      "addressCountry": "US"
    }
  }],
  "image": [
    "https://calendarmedia.blob.core.windows.net/assets/b8be3102-173e-4721-bd74-15f0109147a1-small.jpg"
  ],
  "description": "This workshop will help adjunct faculty become more proficient and effective writers, while also developing reading comprehension and analysis skills.",
  "organizer": {
    "@type": "Organization",
    "name": "Wilmington University",
    "url": "https://www.wilmu.edu"
  },
  "performer": {
    "@type": "Presenter",
    "name": "Wil E Coyote"
  }
}
```

### <a name="faq">FAQ</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/faqpage)
A Frequently Asked Question (FAQ) page contains a list of questions and answers pertaining to a particular topic.
**All FAQS must:**
  - Have a question and answer.

#### <a name="faqparameters"></a>Required and Recommended Parameters

| Property | Type    | Example Value                                                                                                                                                                                             |
| :------- | :------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|          | FAQPage |                                                                                                                                                                                                           |
| Question | Text    | What is the last day to add/drop a class?                                                                                                                                                                 |
| Answer   | Text    | <p>Please refer to the <a href="https://www.wilmu.edu/registrar/changeschedule.aspx">Changing Your Course Schedule page</a> for a full list of drop/add and withdrawal deadlines in the current term.</p> |

#### <a name="faqexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is the last day to add/drop a class?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "<p>Please refer to the <a href=\"https://www.wilmu.edu/registrar/changeschedule.aspx\">Changing Your Course Schedule page</a> for a full list of drop/add and withdrawal deadlines in the current term.</p>"
      }
    },
    {
      "@type": "Question",
      "name": "How long does it take to process a refund?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "We will reimburse you for returned items in the same way you paid for them. For example, any amounts deducted from a gift card will be credited back to a gift card. For returns by mail, once we receive your return, we will process it within 4–5 business days. It may take up to 7 days after we process the return to reflect in your account, depending on your financial institution's processing time."
      }
    }
  ]
}
```

### <a name="howto">How-To</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/how-to)
A How-to walks users through a set of steps to successfully complete a task, featuring video, images, and text <mark>(e.g., video tutorials, register, etc.)</mark>.

#### <a name="howtoparameters"></a>Required and Recommended Parameters

| Property    | Type      | Example Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| :---------- | :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|             | HowTo     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| name        | Text      | How to Prepare for an Advising Appointment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| description | Text      | Get the most out of your time with an academic advisor by completing these steps prior to your appointment.                                                                                                                                                                                                                                                                                                                                                                                                               |
| step        | HowToStep |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| name        | Text      | Review your program requirements in DegreeWorks                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| text        | Text      | <p>Your <a href="https://www.wilmu.edu/advising/myprogram.aspx">DegreeWorks</a> lists all the course requirements for your degree program. Your advisor will use DegreeWorks to review these with you as well, so reviewing this on your own first may help you ask specific questions you may have. If you've not yet, or very recently, submitted your official transcripts for evaluation for transfer credit, your DegreeWorks audit may not have all of your transfer credits applied prior to your appointment.</p> |
| url         | URL       | https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx"                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| position    | Integer   | 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

||HowToStep||
|name|Text|Watch the following instructional videos:|
|url|URL|https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx"|
|position|Integer|2|
||itemListElement||
||VideoObject||
|position|Integer|1|
|name|Text|Learn About Course Schedules and Formats|
|url|URL|https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/ 24054851/partner_id/1582871?iframeembed=true&playerId=kaltura_player&entry_id=1_h3ie83eq&flashvars[localizationCode]=en&flashvars[Kaltura.addCrossoriginToIframe]=true&&wid=1_hcq249h2|
|description|Text|<mark>Video owner will provide.</mark>|
|uploadDate|Date|2022-03-31T08:00-05:00|
|duration|ISO-8601|PT2M21S|
|contentUrl|URL|<mark>How do we get this URL?</mark>|

||VideoObject||
|position|Integer|2|
|name|Text|Scheduling Your WilmU Courses|
|url|URL|https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/ 24054851/partner_id/1582871?iframeembed=true&playerId=kaltura_player&entry_id=1_8umwnacl&flashvars[localizationCode]=en&flashvars[Kaltura.addCrossoriginToIframe]=true&&wid=1_xv0awa49|
|description|Text|<mark>Video owner will provide.|
|uploadDate|Date|2022-03-31T08:00-05:00|
|duration|ISO-8601|PT1M33S|
|contentUrl|URL|<mark>How do we get this URL?</mark>|

||VideoObject||
|position|Integer|3|
|name|Text|Scheduling Do’s and Don’ts|
|url|URL|https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/ 24054851/partner_id/1582871?iframeembed=true&playerId=kaltura_player&entry_id=1_okrt94cv&flashvars[localizationCode]=en&flashvars[Kaltura.addCrossoriginToIframe]=true&&wid=1_i8oxbk6i|
|description|Text|<mark>Video owner will provide.</mark>|
|uploadDate|Date|2022-03-31T08:00-05:00|
|duration|ISO-8601|PT1M03S|
|contentUrl|URL|<mark>How do we get this URL?</mark>|

||HowToStep||
|name|Text|Know Your Responsibilities|
|text|Text|<p>Read the <a href="https://www.wilmu.edu/advising/responsibilities.aspx">Advisor/Student Responsibilities</a> to get an understanding of your own responsibilities when it comes to staying on track for completing your degree.</p>|
|url|URL|https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx"|
|position|Integer|3|

||HowToStep||
|name|Text|Meet the Advisors|
|text|Text|<p>View a <a href="https://www.wilmu.edu/advising/advisors.aspx">list of advisors</a> at each location.</p>|
|url|URL|https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx"|
|position|Integer|4|

#### <a name="howtoexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Prepare for an Advising Appointment",
  "description": "Get the most out of your time with an academic advisor by completing these steps prior to your appointment.",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Review your program requirements in DegreeWorks",
      "text": "<p>Your <a href=\"https://www.wilmu.edu/advising/myprogram.aspx\">DegreeWorks</a> lists all the course requirements for your degree program. Your advisor will use DegreeWorks to review these with you as well, so reviewing this on your own first may help you ask specific questions you may have. If you've not yet, or very recently, submitted your official transcripts for evaluation for transfer credit, your DegreeWorks audit may not have all of your transfer credits applied prior to your appointment.</p>",      
      "url": "https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx",
      "position": "1"
    },
    {
      "@type": "HowToStep",
      "name": "Watch the following instructional videos:",
      "url": "https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx",
      "position": "2",
      "@type": "ItemList",
      "itemListElement": [
        {
          "@type": "VideoObject",
          "position": 1,
          "name": "Learn About Course Schedules and Formats",
          "url": "https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/ 24054851/partner_id/1582871?iframeembed=true&playerId=kaltura_player&entry_id=1_h3ie83eq&flashvars[localizationCode]=en&flashvars[Kaltura.addCrossoriginToIframe]=true&&wid=1_hcq249h2",
          "description": "Enter description here",
          "uploadDate": "2022-03-31T08:00-05:00",
          "duration": "PT2M21S",
          "contentUrl": "Need to discuss, grab video URL within Kaltura??"
        }, 
        {
          "@type": "VideoObject",
          "position": 2,
          "name": "Scheduling Your WilmU Courses",
          "url": "https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/ 24054851/partner_id/1582871?iframeembed=true&playerId=kaltura_player&entry_id=1_8umwnacl&flashvars[localizationCode]=en&flashvars[Kaltura.addCrossoriginToIframe]=true&&wid=1_xv0awa49",
          "description": "Enter description here",
          "uploadDate": "2022-03-31T08:00-05:00",
          "duration": "PT1M33S",
          "contentUrl": "Need to discuss, grab video URL within Kaltura??"
        },
        {
            "@type": "VideoObject",
            "position": 3,
            "name": "Scheduling Do’s and Don’ts",
            "url": "https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/ 24054851/partner_id/1582871?iframeembed=true&playerId=kaltura_player&entry_id=1_okrt94cv&flashvars[localizationCode]=en&flashvars[Kaltura.addCrossoriginToIframe]=true&&wid=1_i8oxbk6i",
            "description": "Enter description here",
            "uploadDate": "2022-03-31T08:00-05:00",
            "duration": "PT1M03S",
            "contentUrl": "Need to discuss, grab video URL within Kaltura??"
          }
      ]
    },
    {
      "@type": "HowToStep",
      "name": "Know Your Responsibilities",
      "url": "https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx",
      "text": "<p>Read the <a href=\"https://www.wilmu.edu/advising/responsibilities.aspx\">Advisor/Student Responsibilities</a> to get an understanding of your own responsibilities when it comes to staying on track for completing your degree.</p>",
      "position": "3"
    },
    {
      "@type": "HowToStep",
      "name": "Meet the Advisors",
      "url": "https://www.wilmu.edu/advising/prepare-for-advising-appointment.aspx",
      "text": "<p>View a <a href=\"https://www.wilmu.edu/advising/advisors.aspx\">list of advisors</a> at each location.</p>",
      "position": "4"
    }
  ]
}
```
### <a name="learningvideo">Learning Video</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/learning-video)
Learning Video markup is intended to give more visibility into the educational contents of the video. The markup can hold information about the various concepts and skills taught in the video.

**All Learning Videos must:**
  - Use the `VideoObject`, `LearningResource` types.
  - Add the `VideoObject` required and recommended properties.
  - The video must be publicly available to watch without a subscription.
  - The total video duration must be a minimum of 30 seconds.
  - Learning Video markup must be added to a page where users can watch the video.
  - Provide at least one of the following properties: `educationalLevel`, `educationalAlignment`, or `learningResourceType`. 
 
#### <a name="learningvideoparameters"></a>Required and Recommended Parameters

| Property             | Type                          | Example Value                                                                                                                                                                    |
| :------------------- | :---------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                      | VideoObject, LearningResource |                                                                                                                                                                                  |
| name                 | Text                          | An introduction to Genetics                                                                                                                                                      |
| description          | Text                          | Explanation of the basics of Genetics for beginners.                                                                                                                             |
| learningResourceType | Text                          | presentation, concept overview[^learnrtnote]                                                                                                                                     |
| educationalLevel     | Text                          | High school (US)                                                                                                                                                                 |
| contentUrl           | URL                           | https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/50196783/partner_id/1582871?iframeembed=true&playerId=kaltura_player_1663075221&entry_id=1_bbvi8zke |
| uploadDate           | Date                          | 2016-03-31T08:00:00+08:00                                                                                                                                                        |
| educationalAlignment | AlignmentObject               |                                                                                                                                                                                  |
| educationalFramework | Text                          | NCLEX                                                                                                                                                                            |
| targetUrl            | URL                           | https://www.ncsbn.org/nclex.page                                                                                                                                                 |
| educationalLevel     | Defined Term, Text, URL       | 10th Grade (AR)[^edlevelnote]                                                                                                                                                    |

[^learnrtnote]: **`learningResourceType` values:**
    - **Concept overview:** The video is explaining a topic or concept.
    - **Problem walkthrough:** The video shows the method or steps to solve an academic problem, such as a math or science word problem.
    - **Real life application:** The video shows how a concept is applied or used in real life.
    - **Activity:** The video shows a demonstration or application of a learning activity, such as an example, an improv game, a concept map, a peer review, or a forced debate.
    - **Science experiment:** The video shows a science experiment.
    - **Lecture:** The video shows a class, lecture, or webinar.
    - **How-to:** The video provides a method or series of steps to do something. For video that are solving procedural STEM problems, use the Problem walkthrough type.
    - **Tips:** The video is sharing tips and tricks.


[^edlevelnote]: **Nonacademic values:**
Only one of these nonacademic values may be specified as educationalLevel.

    Beginner: No prior knowledge is needed to understand the content
    Intermediate: Some knowledge might be needed to understand the content
    Advanced: This content is targeted towards advanced learners that have prior knowledge in the topic

#### <a name="learningvideoexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
  "@type": ["VideoObject", "LearningResource"],
  "name": "An introduction to Genetics",
  "description": "Explanation of the basics of Genetics for beginners.",
  "learningResourceType": "presentation, concept overview",
  "educationalLevel": "High school (US)",
  "contentUrl": "https://cdnapisec.kaltura.com/p/1582871/sp/158287100/embedIframeJs/uiconf_id/50196783/partner_id/1582871?iframeembed=true&playerId=kaltura_player_1663075221&entry_id=1_bbvi8zke",
  "thumbnailUrl": [
    "https://example.com/photos/1x1/photo.jpg",
    "https://example.com/photos/4x3/photo.jpg",
    "https://example.com/photos/16x9/photo.jpg"
  ],
  "uploadDate": "2016-03-31T08:00:00+08:00"
}
```

### <a name="localbusiness">Local Business</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/local-business)
Business details displayed in the Google knowledge panel, including open hours, ratings, directions, and actions to book appointments or order items.
### <a name="logo">Logo</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/logo)
Your organization's logo in search results and Google knowledge panel.

### <a name="person">Person</a>

#### <a name="personparameters"></a>Required and Recommended Parameters

| Property  | Type             | Example Value                           |
| :-------- | :--------------- | :-------------------------------------- |
|           | Person           |                                         |
| name      | Text             | Jane Doe                                |
| jobTitle  | Text             | Director                                |
| telephone | Text             | (302) 123-4567                          |
| email     | Text             | mailto:jane-doe@wilmu.edu               |
| image     | ImageObject, URL | https://www.wilmu.edu/images/person.png |
| url       | URL              | https://www.wilmu.edu/dept/             |
#### <a name="personexample"></a>Example Code

```json
{
  "@context": "https://schema.org/",
  "@type": "Person",
  "name": "Jane Doe",
  "jobTitle": "Director",
  "telephone": "(302) 123-4567",
  "email": "mailto:jane-doe@wilmu.edu",
  "image": "https://www.wilmu.edu/images/person.png",
  "url": "https://www.wilmu.edu/dept/"
}
```

### <a name="qa">Q&A</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/qapage)
Q&A Pages are web pages that contain data in a question and answer format, which is one question followed by its answers.
### <a name="searchbox">Sitelinks Search box</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/sitelinks-searchbox)
A search box that is scoped to your website when it appears as a search result.
#### <a name="searchboxparameters"></a>Required and Recommended Parameters

| Property        | Type            | Example Value                                                         |
| :-------------- | :-------------- | :-------------------------------------------------------------------- |
| potentialAction | Action          | SearchAction                                                          |
| target          | EntryPoint, URL | EntryPoint                                                            |
| urlTemplate     | Text            | https://www.wilmu.edu/gcse-search-results.aspx?q={search_term_string} |
| query-input     | Duration        | required name=search_term_string                                      |

#### <a name="searchboxexample"></a>Example Code

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "url": "https://www.wilmu.edu/",
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://www.wilmu.edu/gcse-search-results.aspx?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
```
### <a name="speakable">Speakable</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/speakable)
<mark>TTS, read news stories??</mark>

### <a name="video">Video</a> - [Reference](https://developers.google.com/search/docs/appearance/structured-data/video)
Video information in search results, with the option to play the video, specify video segments, and live-stream content.

 [Back to top](#top) 

