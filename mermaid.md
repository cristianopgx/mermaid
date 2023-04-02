classDiagram
direction BT
class action_plans {
   varchar(128) description
   date start_date
   date due_date
   varchar(128) cost
   numeric progress
   bigint alert_id
   bigint person_id
   timestamp(6) created_at
   timestamp(6) updated_at
   timestamp(6) deleted_at
   bigint tenant_id
   bigint id
}
class activities {
   varchar name
   varchar slug
   text description
   bigint occupation_id
   bigint activity_group_id
   bigint activity_subgroup_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class activity_groups {
   varchar type
   varchar name
   varchar slug
   text description
   bigint occupation_id
   bigint activity_group_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class addresses {
   varchar label
   varchar street
   varchar number
   varchar complement
   varchar neighborhood
   varchar postal_code
   varchar city
   varchar state
   varchar country
   bigint person_id
   bigint tenant_id
   bigint billing_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class administrators {
   varchar email
   varchar encrypted_password
   timestamp(6) remember_created_at
   varchar first_name
   varchar last_name
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint user_id
   varchar full_name
   integer kind
   bigint[] tenant_ids
   bigint id
}
class alert_automatics {
   integer subpriority
   bigint collective_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint occupation_seat_id
   bigint occupation_id
   bigint tenant_id
   bigint id
}
class alert_manuals {
   integer kind
   varchar priority_justification
   varchar title
   varchar description
   bigint collective_id
   bigint person_id
   bigint occupation_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class alerts {
   integer status
   integer priority
   timestamp(6) opened_at
   bigint collective_id
   varchar alertable_type
   bigint alertable_id
   timestamp(6) created_at
   timestamp(6) updated_at
   text justification
   text solve_method
   timestamp(6) justified_at
   timestamp(6) solved_at
   integer action_plans_count
   timestamp(6) first_action_plan_created_at
   timestamp(6) deleted_at
   bigint tenant_id
   bigint id
}
class ar_internal_metadata {
   varchar value
   timestamp(6) created_at
   timestamp(6) updated_at
   varchar key
}
class autonomy_mappings {
   varchar type
   integer status
   integer person_status
   integer responsible_status
   double precision responsible_score
   jsonb responsible_dimensions_scores
   double precision person_score
   jsonb person_dimensions_scores
   double precision score
   double precision disagreement_score
   jsonb dimensions_disagreements_scores
   bigint person_id
   bigint responsible_id
   bigint activity_id
   bigint occupation_id
   bigint occupation_mapping_id
   timestamp(6) created_at
   timestamp(6) updated_at
   boolean undetermined_autonomy
   boolean undetermined_disagreement
   integer specificity
   double precision activity_disagreements_high_percentage
   bigint manager_id
   boolean has_new_dimensions
   timestamp(6) last_person_publish_at
   timestamp(6) last_responsible_publish_at
   date person_start_date
   varchar person_justification
   varchar responsible_justification
   integer disagreement_level
   boolean in_odt
   boolean locked_results
   integer high_disagreement_type
   boolean currently_seated
   bigint tenant_id
   bigint id
}
class autonomy_pattern_dimensions {
   varchar label
   integer kind
   varchar description
   integer position
   bigint autonomy_pattern_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class autonomy_pattern_levels {
   integer level
   varchar label
   bigint dimension_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class autonomy_patterns {
   integer status
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class billings {
   varchar cnpj
   varchar corporate_name
   varchar responsible_name
   varchar responsible_phone
   varchar responsible_email
   text observations
   bigint tenant_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class collectives {
   varchar name
   varchar slug
   varchar type
   varchar ancestry
   integer kind
   bigint workplace_id
   bigint manager_seat_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint work_shift_id
   jsonb occupations_sections_ids
   varchar manager_ancestry
   timestamp(6) deleted_at
   double precision autonomy_average_score
   bigint tenant_id
   bigint id
}
class companies {
   varchar type
   varchar corporate_name
   varchar fantasy_name
   varchar cnpj
   varchar phone
   varchar contract_manager_name
   varchar contract_manager_email
   varchar contract_manager_phone
   varchar state_registration
   varchar municipal_registration
   varchar image_url
   bigint plan_id
   timestamp(6) created_at
   timestamp(6) updated_at
   varchar slug
   bigint tenant_id
   bigint id
}
class companies_users {
   integer role
   bigint company_id
   bigint user_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class contracts {
   integer category
   integer kind
   varchar corporate_registration
   date start_date
   date end_date
   boolean substitute
   varchar icon
   bigint person_id
   timestamp(6) created_at
   timestamp(6) updated_at
   varchar name
   varchar slug
   varchar initials
   bigint tenant_id
   bigint id
}
class data_histories {
   varchar modified_model_name
   integer changed_object_id
   jsonb changed_object_data
   timestamp(6) created_at
   timestamp(6) updated_at
   timestamp(6) deleted_at
   bigint tenant_id
   bigint id
}
class data_migrations {
   varchar version
}
class delayed_jobs {
   integer priority
   integer attempts
   text handler
   text last_error
   timestamp(6) run_at
   timestamp(6) locked_at
   timestamp(6) failed_at
   varchar locked_by
   varchar queue
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class documents {
   varchar title
   varchar description
   varchar url
   integer kind
   bigint expanded_collective_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class emphases {
   varchar name
   varchar slug
   text description
   bigint occupation_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class emphases_people {
   bigint emphasis_id
   bigint person_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class history_kpis {
   jsonb alert_priorities
   jsonb alert_treatments
   jsonb critical_functions
   jsonb autonomy_levels
   jsonb mapping_status
   jsonb expertise_odt
   jsonb management_personnel
   bigint collective_id
   timestamp(6) created_at
   timestamp(6) updated_at
   jsonb alert_details
   date date_register
   bigint id
}
class imports {
   integer status
   integer file_extension
   varchar file_url
   timestamp(6) confirmed_at
   timestamp(6) started_at
   timestamp(6) finished_at
   jsonb people_data
   bigint user_id
   timestamp(6) created_at
   timestamp(6) updated_at
   varchar file_name
   bigint tenant_id
   bigint id
}
class job_titles {
   varchar name
   varchar slug
   timestamp(6) created_at
   timestamp(6) updated_at
   boolean in_odt
   bigint tenant_id
   bigint id
}
class kpis {
   jsonb alert_priorities
   jsonb alert_details
   jsonb alert_treatments
   jsonb critical_functions
   jsonb autonomy_levels
   jsonb mapping_status
   jsonb expertise_odt
   jsonb management_personnel
   bigint collective_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class mobility_string_translations {
   varchar locale
   varchar key
   varchar value
   varchar translatable_type
   bigint translatable_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class mobility_text_translations {
   varchar locale
   varchar key
   text value
   varchar translatable_type
   bigint translatable_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class occupations {
   varchar name
   varchar slug
   text description
   bigint focal_point_id
   timestamp(6) created_at
   timestamp(6) updated_at
   boolean in_odt
   bigint tenant_id
   bigint id
}
class occupations_seats {
   double precision planned_autonomy_score
   integer dedication_percentage
   integer[] emphasis_ids
   bigint occupation_id
   bigint seat_id
   bigint workplace_id
   timestamp(6) created_at
   timestamp(6) updated_at
   timestamp(6) deleted_at
   bigint tenant_id
   bigint id
}
class people {
   varchar first_name
   varchar last_name
   varchar nickname
   varchar profile_picture_url
   varchar corporate_email
   varchar corporate_phone
   varchar personal_email
   varchar personal_phone
   varchar internal_phone
   date birthdate
   varchar birthplace
   varchar cpf
   varchar identity_card
   boolean disability
   integer contract_type
   integer availability_type
   bigint job_title_id
   bigint main_seat_id
   timestamp(6) created_at
   timestamp(6) updated_at
   boolean manager
   varchar ancestry
   bigint third_party_company_id
   bigint import_id
   varchar full_name
   varchar social_name
   varchar work_unity
   varchar management
   bigint work_shift_id
   varchar direct_manager_cpf
   boolean in_odt
   integer action_plans_count
   bigint tenant_id
   bigint id
}
class pg_search_documents {
   text content
   varchar searchable_type
   bigint searchable_id
   timestamp(6) created_at
   timestamp(6) updated_at
   tsvector searchable_tsvector
   bigint id
}
class plans {
   varchar name
   varchar slug
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class preferences {
   varchar key
   varchar slug
   text value
   bigint user_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class schema_migrations {
   varchar version
}
class seats {
   varchar name
   varchar slug
   integer dedication_percentage
   integer position_type
   integer employee_type
   integer occupation_type
   integer contract_type
   integer availability_type
   integer flow_type
   boolean count_in_headcount
   jsonb metadata
   bigint collective_id
   bigint person_id
   bigint third_party_company_id
   bigint substitute_for_id
   timestamp(6) created_at
   timestamp(6) updated_at
   integer status
   bigint workplace_id
   bigint work_shift_id
   bigint other_contract_id
   integer occupations_section_index
   timestamp(6) deleted_at
   bigint tenant_id
   bigint id
}
class tenants {
   varchar(64) name
   varchar(64) fantasy_name
   varchar registration_number
   varchar phone
   varchar(256) email
   varchar image_url
   integer status
   bigint plan_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class users {
   varchar provider
   varchar uid
   varchar encrypted_password
   varchar reset_password_token
   timestamp(6) reset_password_sent_at
   boolean allow_password_change
   timestamp(6) forgot_username_sent_at
   timestamp(6) remember_created_at
   integer sign_in_count
   timestamp(6) current_sign_in_at
   timestamp(6) last_sign_in_at
   inet current_sign_in_ip
   inet last_sign_in_ip
   varchar confirmation_token
   timestamp(6) confirmed_at
   timestamp(6) confirmation_sent_at
   varchar unconfirmed_email
   timestamp(6) email_confirmed_at
   varchar unconfirmed_phone
   varchar encrypted_phone_confirmation_token
   varchar encrypted_phone_confirmation_token_iv
   timestamp(6) phone_confirmed_at
   timestamp(6) phone_confirmation_sent_at
   varchar phone_confirmation_message
   varchar email
   varchar username
   varchar phone
   json tokens
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint person_id
   integer status
   varchar nickname
   integer kind
   varchar full_name
   boolean terms_of_use_accepted
   boolean privacy_policy_accepted
   integer locale
   bigint id
}
class versions {
   varchar item_type
   bigint item_id
   varchar event
   jsonb object
   jsonb object_changes
   bigint whodunnit
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint id
}
class work_schedules {
   integer weekday
   integer start_hour
   integer end_hour
   bigint work_shift_id
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}
class work_shifts {
   varchar label
   integer start_hour
   integer end_hour
   timestamp(6) created_at
   timestamp(6) updated_at
   integer start_minute
   integer end_minute
   varchar slug
   bigint tenant_id
   bigint id
}
class workplaces {
   varchar name
   varchar slug
   timestamp(6) created_at
   timestamp(6) updated_at
   bigint tenant_id
   bigint id
}

action_plans  -->  alerts : alert_id:id
action_plans  -->  people : person_id:id
action_plans  -->  tenants : tenant_id:id
activities  -->  activity_groups : activity_group_id:id
activities  -->  occupations : occupation_id:id
activities  -->  tenants : tenant_id:id
activity_groups  -->  activity_groups : activity_group_id:id
activity_groups  -->  occupations : occupation_id:id
activity_groups  -->  tenants : tenant_id:id
addresses  -->  billings : billing_id:id
addresses  -->  people : person_id:id
addresses  -->  tenants : tenant_id:id
administrators  -->  users : user_id:id
alert_automatics  -->  collectives : collective_id:id
alert_automatics  -->  occupations : occupation_id:id
alert_automatics  -->  tenants : tenant_id:id
alert_manuals  -->  collectives : collective_id:id
alert_manuals  -->  occupations : occupation_id:id
alert_manuals  -->  people : person_id:id
alert_manuals  -->  tenants : tenant_id:id
alerts  -->  collectives : collective_id:id
alerts  -->  tenants : tenant_id:id
autonomy_mappings  -->  activities : activity_id:id
autonomy_mappings  -->  occupations : occupation_id:id
autonomy_mappings  -->  people : person_id:id
autonomy_mappings  -->  tenants : tenant_id:id
autonomy_pattern_dimensions  -->  autonomy_patterns : autonomy_pattern_id:id
autonomy_pattern_dimensions  -->  tenants : tenant_id:id
autonomy_pattern_levels  -->  tenants : tenant_id:id
autonomy_patterns  -->  tenants : tenant_id:id
billings  -->  tenants : tenant_id:id
collectives  -->  tenants : tenant_id:id
collectives  -->  work_shifts : work_shift_id:id
collectives  -->  workplaces : workplace_id:id
companies  -->  plans : plan_id:id
companies  -->  tenants : tenant_id:id
companies_users  -->  companies : company_id:id
companies_users  -->  tenants : tenant_id:id
companies_users  -->  users : user_id:id
contracts  -->  people : person_id:id
contracts  -->  tenants : tenant_id:id
data_histories  -->  tenants : tenant_id:id
documents  -->  tenants : tenant_id:id
emphases  -->  occupations : occupation_id:id
emphases  -->  tenants : tenant_id:id
emphases_people  -->  emphases : emphasis_id:id
emphases_people  -->  people : person_id:id
emphases_people  -->  tenants : tenant_id:id
history_kpis  -->  collectives : collective_id:id
imports  -->  tenants : tenant_id:id
imports  -->  users : user_id:id
job_titles  -->  tenants : tenant_id:id
kpis  -->  collectives : collective_id:id
kpis  -->  tenants : tenant_id:id
occupations  -->  tenants : tenant_id:id
occupations_seats  -->  occupations : occupation_id:id
occupations_seats  -->  seats : seat_id:id
occupations_seats  -->  tenants : tenant_id:id
occupations_seats  -->  workplaces : workplace_id:id
people  -->  imports : import_id:id
people  -->  job_titles : job_title_id:id
people  -->  tenants : tenant_id:id
people  -->  work_shifts : work_shift_id:id
preferences  -->  tenants : tenant_id:id
preferences  -->  users : user_id:id
seats  -->  collectives : collective_id:id
seats  -->  people : person_id:id
seats  -->  tenants : tenant_id:id
seats  -->  work_shifts : work_shift_id:id
seats  -->  workplaces : workplace_id:id
tenants  -->  plans : plan_id:id
users  -->  people : person_id:id
work_schedules  -->  tenants : tenant_id:id
work_schedules  -->  work_shifts : work_shift_id:id
work_shifts  -->  tenants : tenant_id:id
workplaces  -->  tenants : tenant_id:id
