# HibernateGenerationType.SEQUENCEPrimaryKeyGenerationStrategy

Hibernate GenerationType.SEQUENCE primary key generation strategy

GenerationType.SEQUENCE

The GenerationTye.SEQUENCE is also way to generate primary key values and uses a database sequence to generate unique values.

It requires additional select statements to get the next value from a database sequence.

But this has no performance impact for most applications. And if your application has to persist a huge number of new entities, you can use some Hibernate specific optimmizations to reduce the number of statements. 

@Id

@Column(name=”employee_id”)

@GeneratedValue(strategy=GenerationType.SEQUENCE)

Private Integer employeeId;

If you don’t provide any additional information, Hibernate will request the next value from its default seequece. You can change that by referencing the name of a @SequenceGenerator in the generator attribute of the @GeneratedValue annotation. The @SequenceGenerator annotation lets you define the name of the generator, the name, the schema of the database sequence and the allocation size of the sequence.

@Id

@Column(name=”employee_id”)

@GeneratedValue(strategy=GenerationType.SEQUENCE, generator = “empid_generator”)

@SequenceGenerator(name=”empid_generator”, sequenceName=”empid_seq”, allocationSize=1)

Private Integer employeeId;
