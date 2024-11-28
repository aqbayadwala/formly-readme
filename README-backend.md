# Formly2 Backend



### Prerequisites

Here is what you need to be able to run formly

- Node.js
- Xampp (Version=8.0.30)
- pnpm

### Steps to setup this project locally
1. Install [XAMPP](https://www.apachefriends.org/download.html)

2. Clone the repo [https://github.com/Bitkraft-Technologies-LLP/formly2-backend.git]() 
    ```
    git clone  https://github.com/Bitkraft-Technologies-LLP/formly2-backend.git
    ```
3. Copy the .env file provided by the administrator
4. Go to current sprint branch
    ```
    git checkout -b <sprint branch>
    ```
5. Start XAMPP - Apache and MySQL server
    -   [Linux FAQs for XAMPP](https://www.apachefriends.org/faq_linux.html)
    -   [Windows FAQs for XAMPP](https://www.apachefriends.org/faq_windows.html)
    -   [OS X FAQs for XAMPP](https://www.apachefriends.org/faq_osx.html)
6. Install pnpm using npm
    ```
    npm i -g pnpm
    ```
7. Install dependencies

    ```
    pnpm i
    ```
8. Create database: formly2_dev from [PhpMyAdmin](http://localhost/phpmyadmin)
9.  Create a schema
    ```
    pnpm migration:generate
    ```
10. Push the schema to the database
    ```
    pnpm migration:push
    ```
12. Insert these records into the database from [PhpMyAdmin](http://localhost/phpmyadmin)

    ```sql
    INSERT INTO `question_category` 
    (`name`, `order`) 
    VALUES 
    ('inputs', 1),
    ('choices', 2),
    ('rating_&_ranking', 3),
    ('form_structure', 4),
    ('contact', 5),
    ('media', 6),
    ('payment', 7);
    ```
    ```sql
    INSERT INTO `question_master` 
    (`name`, `question_title_placeholder`, `question_description_placeholder`, `type`, `question_category_id`) 
    VALUES 
    ('short_text', 'Question text here. Recall information with @', 'Description (optional)', 1, 1),
    ('long_text', 'Question text here. Recall information with @', 'Description (optional)', 2, 1),
    ('date_&_time', 'Question text here. Recall information with @', 'Description (optional)', 3, 1),
    ('number', 'Question text here. Recall information with @', 'Description (optional)', 4, 1),
     
    ('multiple_choice', 'Question text here. Recall information with @', 'Description (optional)', 5, 2),
    ('dropdown', 'Question text here. Recall information with @', 'Description (optional)', 6, 2),
    ('image_choice', 'Question text here. Recall information with @', 'Description (optional)', 7, 2),
    ('two_choices', 'Question text here. Recall information with @', 'Description (optional)', 8, 2),
     
    ('slider', 'Question text here. Recall information with @', 'Description (optional)', 9, 3),
    ('rating', 'Question text here. Recall information with @', 'Description (optional)', 10, 3),
    ('opinion_scale', 'Question text here. Recall information with @', 'Description (optional)', 11, 3),
    ('matrix', 'Question text here. Recall information with @', 'Description (optional)', 12, 3),
     
    ('section', 'Section title here. Recall information with @', 'Description (optional)', 13, 4),
    ('statement', 'Question text here. Recall information with @', 'Description (optional)', 14, 4),
    ('welcome_screen', 'Welcome text here!', 'Description (optional)', 15, 4),
    ('redirect_to_URL', 'Question text here. Recall information with @', 'Description (optional)', 16, 4),
    ('thank_you_screen', 'Thank you! Recall information with @', 'Description (optional)', 17, 4),
     
    ('email', 'Question text here. Recall information with @', 'Description (optional)', 18, 5),
    ('phone_number', 'Question text here. Recall information with @', 'Description (optional)', 19, 5),
    ('website', 'Question text here. Recall information with @', 'Description (optional)', 20, 5),
     
    ('signature', 'Question text here. Recall information with @', 'Description (optional)', 21, 6),
    ('file_upload', 'Question text here. Recall information with @', 'Description (optional)', 22, 6),
     
    ('payment', 'Question text here. Recall information with @', 'Description (optional)', 23, 7);
    ```
    ```sql
    INSERT INTO form_theme (name, details, type) VALUES 
    ('Black Theme', '{"questionColor":"#37404A","answerColor":"#5c5c5c","buttonColor":"#37404A"}', 0),
    ('Blue theme', '{"questionColor": "#3C49DA", "answerColor": "#2134ff", "buttonColor": "#4452C6"}', 0),
    ('Green theme', '{"questionColor": "#2A9D4D", "answerColor": "#35B729", "buttonColor": "#7DBB91"}', 0),
    ('Red theme', '{"questionColor": "#FF1808", "answerColor": "#DC3125", "buttonColor": "#A1362F"}', 0),
    ('Yellow theme', '{"questionColor": "#B89837", "answerColor": "#E6B933", "buttonColor": "#E4BA3F"}', 0),
    ('White theme', '{"questionColor": "#FFFFFF", "answerColor": "#FFFFFF", "buttonColor": "#FBFBFB"}', 0);
    ```
    ```sql
    INSERT INTO `subscription_master` 
    (`name`, `usd_monthly_price`, `usd_annual_price`, `gbp_monthly_price`, `gbp_annual_price`,
    `max_custom_domain_entries_limit`, `max_storage_limit_in_mb`, `max_responses_per_month`,
    `max_workspace_limit`, `max_file_upload_size_limit`, `max_form_limit`,
    `max_questions_per_form_limit`, `max_payments_limit`, `allow_subdomain` ,
    `allow_custom_logo`, `allow_redirect_to_url`,`allow_remove_formly_branding`,
    `allow_verify_respondent_email`, `allow_email_notifications`, `is_upgradable`) 
    VALUES 
    ('Free', 0.00, 0.00, 0.00, 0.00,
    0, 200, 100, 
    1, 10, 3,
    15, 10, 0,
    0, 0, 0,
    0, 0, 1),
    
    ('Silver', 19.00, 190.00, 16.00, 160.00,
    0, 2048, 1000,
    3, 10, -1,
    -1, 20, 0,
    0, 0, 0,
    0, 1, 1),
    
    ('Gold', 29.00, 290.00, 25.00, 250.00,
    10, 4096, -1,
    10, 20, -1,
    -1, -1, 1,
    1, 1, 1,
    1, 1, 1),
    
    ('Enterprise', 29.00, 290.00, 25.00, 250.00,
    -1, 4096, -1,
    -1, 500, -1,
    -1, -1, 1,
    1, 1, 1,
    1, 1, 0),
    
    ('Lifetime', 29.00, 290.00, 25.00, 250.00,
    -1, 4096, -1,
    -1, 500, -1,
    -1, -1, 1,
    1, 1, 1,
    1, 1, 0)
    ```
    ```sql
    INSERT INTO `service_master`(service_name, service_description, status, is_deleted, created_date, created_by, updated_date, updated_by, deleted_date, deleted_by, remarks
    ) values (
        'google_sheet', 'Integration for google sheet', 0, 0, UNIX_TIMESTAMP(), 0, 0, 0, 0,0, 'This is a remark'
    );
    ```

13. Start the development server
    ```
    pnpm start:dev
    ```