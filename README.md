# trialtech
DB DESIGN
title Entity-Diagram of Trialtech DB
// define tables
users [icon: user, color: blue] {
  id string pk
  email string
  password string
  role string
}

Lawyer [icon: user, color: red] {
  id string pk
  email string
  name string
  phno string
  address string
  type string
  court_area string
  past_case_st string
  present_case_st string
 
}

undertrial_prisoner [icon: user, color: orange] {
  id string pk
  email string
  name string
  phno string
  address string
  case_st string
  bail_consideration boolean

}

jail_authority [icon: user-secret, color: green] {
  id string pk
  email string
  bail_consideration boolean
  
  lawyer_id string fk
}

NGO [icon: users, color: purple] {
  id string pk
  name string
  contact_info string
  address string
}
// End of tables


// define relationships
users.id <> Lawyer.id
users.id <> undertrial_prisoner.id
users.id <> jail_authority.id
jail_authority  < undertrial_prisoner.id
jail_authority.lawyer_id <> Lawyer.id
Lawyer <  undertrial_prisoner.id
undertrial_prisoner.lawyer_id > Lawyer.id
Lawyer.id <> jail_authority.lawyer_id
NGO.id <> undertrial_prisoner.id
