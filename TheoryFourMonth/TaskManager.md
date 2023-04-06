# Full program four month + coding

---

**Navigation Types** (Типы навигации) - это механизм, который позволяет пользователям перемещаться между различными экранами приложения. В **Android** есть несколько типов навигации, таких как **Bottom Navigation,** **Navigation Drawer** и т.д. Они позволяют легко и интуитивно перемещаться по приложению.

Пример использования **Bottom Navigation:**

**kotlin:**

**class MainActivity : AppCompatActivity() {**

    private lateinit var navController: NavController

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val navHostFragment = supportFragmentManager.findFragmentById(R.id.nav_host_fragment) as NavHostFragment
        navController = navHostFragment.navController

        val bottomNav = findViewById<BottomNavigationView>(R.id.bottom_nav)
        bottomNav.setupWithNavController(navController)
    }
**}**

---

**ViewPager** - это виджет, который позволяет пользователю легко просматривать множество различных фрагментов на одном экране. Он может использоваться для создания слайд-шоу, галереи изображений и т.д.

Пример использования **ViewPager:**

**kotlin:**

**class MainActivity : AppCompatActivity() {**

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val viewPager = findViewById<ViewPager>(R.id.view_pager)
        val adapter = MyPagerAdapter(supportFragmentManager)
        viewPager.adapter = adapter
    }

    class MyPagerAdapter(fm: FragmentManager) : FragmentPagerAdapter(fm) {

        override fun getCount(): Int {
            return 3
        }

        override fun getItem(position: Int): Fragment {
            **return when (position) {
                0 -> FirstFragment()
                1 -> SecondFragment()
                2 -> ThirdFragment()
                **else -> throw IllegalArgumentException("Invalid position: $position")
            }
        }
    }
**}**

---

**SharedPreferences** - это механизм для хранения небольших объемов данных, таких как настройки пользователя, на устройстве **Android.** Они сохраняются в формате ключ-значение, и могут быть легко получены и изменены в любой части приложения.

Пример использования SharedPreferences:

**kotlin:**

**val sharedPreferences = getSharedPreferences("my_preferences", Context.MODE_PRIVATE)**
**val editor = sharedPreferences.edit()**
**editor.putString("username", "John")**
**editor.putInt("age", 30)**
**editor.apply()**

**val username = sharedPreferences.getString("username", null)**
**val age = sharedPreferences.getInt("age", 0)**

---

База данных **(Database)** - это набор связанных данных, организованных для удобного использования и доступа.

В мобильном приложении база данных может использоваться для хранения информации, которую пользователь может добавлять, изменять или удалять. Например, список задач, заметки, контакты, настройки приложения и т.д.

В **Android** для работы с базами данных используется фреймворк **SQLite.** Для упрощения работы с базами данных существует множество сторонних библиотек, таких как **Room,** **GreenDAO,** **Realm** и т.д.

Пример работы с базой данных с использованием **Room:**

**1.Создание модели данных:**

**@Entity(tableName = "users")**
**data class User(**
**@PrimaryKey(autoGenerate = true)**
**val id: Long = 0,**
**val name: String,**
**val age: Int**
**)**


**2.Создание интерфейса для работы с базой данных:**

**kotlin:**

**@Dao**
**interface UserDao {**
**@Insert**
**suspend fun insert(user: User)**
**@Query("SELECT * FROM users")**
**suspend fun getAllUsers(): List<User>**
**}**

**Создание базы данных:**

**kotlin:**

**@Database(entities = [User::class], version = 1)**
**abstract class AppDatabase : RoomDatabase() {**
**abstract fun userDao(): UserDao**
**}**

**4.Использование базы данных в приложении:**

**kotlin:**

**val db = Room.databaseBuilder(**
**applicationContext,**
**AppDatabase::class.java, "my-db"**
**).build()**

**val userDao = db.userDao()**
**userDao.insert(User(name = "John", age = 25))**

**val users = userDao.getAllUsers()**

---

**Design** - это набор рекомендаций и готовых компонентов для создания красивого и удобного пользовательского интерфейса.

В **Android** для создания пользовательского интерфейса используется фреймворк **Android UI.** Для упрощения создания дизайна существует множество сторонних библиотек, таких как **Material Design, Flexbox Layout, ConstraintLayout** и т.д.

---

**Firebase** - это платформа от **Google,** которая предоставляет широкий спектр инструментов и сервисов для разработки мобильных и веб-приложений. **Firebase** включает в себя множество инструментов, таких как аутентификация пользователей, базы данных, хранилища файлов, облачные функции, аналитику, тестирование и другие сервисы.

---

**Firebase Firestore** - это **NoSQL** документо-ориентированная база данных, которая предоставляет быстрый и масштабируемый способ хранения и синхронизации данных в приложениях. **Firestore** использует облачную инфраструктуру **Firebase** и обеспечивает автоматическую синхронизацию данных между клиентами приложения.

---

**Push-уведомления** - это способ отправки сообщений на мобильное устройство пользователей без необходимости открытия приложения. **Push-уведомления** могут быть использованы для уведомления пользователей о новых сообщениях, обновлениях, событиях и других событиях, которые могут быть интересны пользователю. **Firebase** предоставляет инструменты для отправки **push-уведомлений** на мобильные устройства пользователей.

---
