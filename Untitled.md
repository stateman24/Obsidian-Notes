this my Creator Profile entity code and it respecive interface

export class CreatorProfileEntity {
  constructor(
    public id: string,
    public userId: string,
    public firstName?: string,
    public lastName?: string,
    public CV?: string,
    public bio?: string,
    public portfolioWebsite?: string,
    public phone?: string,
    public location?: string,
    public hourlyRate?: string,
    public workMode?: WorkMode,
    public availability?: Availability,
    public skills?: ISkill[],
    public experience?: Experience,
    public portfolio?: string,
    public rating?: number,
    public certification?: ICertificationEntity[],
    public education?: IEducationEntity[],
    public employment?: IEmploymentEntity[],
  ) {}


  static fromObject(obj: ICreatorProfileEntity): CreatorProfileEntity {
    const { id, userId } = obj;

    if (!id) throw new ValidationError('Missing id');
    if (!userId) throw new ValidationError('Missing creatorId');

    return new CreatorProfileEntity(id, userId);
  }
}

export interface ICreatorProfileEntity extends Partial<CreatorProfile> {
  id: string;
  userId: string;
  firstName?: string;
  lastName?: string;
  CV?: string;
  bio?: string;
  portfolioWebsite?: string;
  phone?: string;
  location?: string;
  hourlyRate?: number;
  workMode?: WorkMode;
  availability?: Availability;
  skills?: ISkill[];
  experience?: Experience;
  portfolio?: string;
  rating?: number;
  certification?: ICertificationEntity[];
  education?: IEducationEntity[];
  employment?: IEmploymentEntity[];
}

Since I am working  clean architecture I want to write the abstract of the repository and datasoruce for creator profile in the domain layer so that I can make the implementation in the the infrastructure layer, also I am using prisma as my ORM.the repository code should be like this 

export abstract class UserRepository {
  abstract findUserById(id: string): Promise<UserEntity | null>;
  abstract findUserByEmail(email: string): Promise<UserEntity | null>;
  abstract createUser(registerUserDto: RegisterUserDto): Promise<UserEntity>;
}

the datasource should be like this 
export abstract class UserDatasource {
  abstract findUserById(id: string): Promise<UserEntity | null>;
  abstract findUserByEmail(email: string): Promise<UserEntity | null>;
  abstract createUser(registerUserDto: RegisterUserDto): Promise<UserEntity>;
}

So I want the repository and datasource abstact should do CRUD operations for the creator profile 
