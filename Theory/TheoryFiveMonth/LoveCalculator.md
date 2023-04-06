# Full programs five month theory

---

**MVP** **(Model-View-Presenter)** - это архитектурный подход, который разделяет приложение на три части: модель **(Model),** представление **(View)** и презентер **Presenter).** Модель содержит данные и логику приложения, представление - отображает данные пользователю, а презентер обрабатывает действия пользователя и взаимодействует с моделью и представлением. В **MVP**-подходе модель и представление не взаимодействуют напрямую, а через презентер.

Пример кода для **MVP**-подхода:

**kotlin:**

**interface MainContract {**
**interface View {**
**fun showData(data: String)**
**}**

**interface Presenter {**
**fun loadData()**
**}**

**class MainActivity : AppCompatActivity(), MainContract.View {**
**private lateinit var presenter: MainContract.Presenter**

**override fun onCreate(savedInstanceState: Bundle?) {**
**super.onCreate(savedInstanceState)**
**setContentView(R.layout.activity_main)**
**presenter = MainPresenter(this)**
**presenter.loadData()**
**}**

**override fun showData(data: String) {**
**// отображение данных**
**}**

**}**

**class MainPresenter(private val view: MainContract.View) : MainContract.Presenter {**
**override fun loadData() {**
**// получение данных из модели**
**val data = Model.getData()**
**// передача данных в представление**
**view.showData(data)**
**}**
**}**

---

**Retrofit** - это библиотека для работы с **HTTP-запросами в Android.** Она позволяет легко создавать клиентские приложения, которые могут взаимодействовать с сервером через **API.**

Пример настройки **Retrofit** для получения данных из удаленного источника:

**interface ApiService {**
**@GET("data")**
**fun getData(): Call<Data>**
**}**

**object ApiClient {**
**private const val BASE_URL = "https://example.com/"**
**private var apiService: ApiService? = null**
**fun getApiService(): ApiService {**
**if (apiService == null) {**
**val retrofit = Retrofit.Builder()**
**.baseUrl(BASE_URL)**
**.addConverterFactory(GsonConverterFactory.create())**
**.build()**

        apiService = retrofit.create(ApiService::class.java)
    }

    return apiService!!
}
**}**

**class MainPresenter(private val view: MainContract.View) : MainContract.Presenter {**
**override fun loadData() {**
**val apiService = ApiClient.getApiService()**
**val call = apiService.getData()**
**call.enqueue(object : Callback<Data> {**
**override fun onResponse(call: Call<Data>, response: Response<Data>) {**
**if (response.isSuccessful) {**
**val data = response.body()**
**// передача данных в представление**
**view.showData(data.toString())**
**}**
**}**
**override fun onFailure(call: Call<Data>, t: Throwable) {**
**// обработка ошибки
**}**
**})**
**}**
**}**

---

**ViewPager2** - это компонент пользовательского интерфейса в **Android,** который позволяет легко создавать экраны с возможностью горизонтальной прокрутки между несколькими фрагментами или представлениями. **ViewPager2** имеет более удобный **API,** чем его предшественник - **ViewPager.**

Пример использования **ViewPager2** в **XML-макете:**

**<androidx.viewpager2.widget.ViewPager2**
**android:id="@+id/viewPager2"**
**android:layout_width="match_parent"**
**android:layout_height="match_parent"/>**

Пример настройки **ViewPager2** в коде:

**kotlin:**

**class MainActivity : AppCompatActivity() {**
**private lateinit var viewPager2: ViewPager2**
**override fun onCreate(savedInstanceState: Bundle?) {**
**super.onCreate(savedInstanceState)**
**setContentView(R.layout.activity_main)**
**viewPager2 = findViewById(R.id.viewPager2)**
**viewPager2.adapter = MyAdapter(this)**
**}**

**private class MyAdapter(fragmentActivity: FragmentActivity) :**
**FragmentStateAdapter(fragmentActivity) {**

    override fun getItemCount(): Int {
        // количество страниц
        return 3
    }

    override fun createFragment(position: Int): Fragment {
        // создание фрагмента для позиции position
        return MyFragment()
    }
**}**

**MVVM (Model-View-ViewModel)** - это архитектурный подход, который разделяет приложение на три части: модель **(Model), представление (View)** и модель представления **(ViewModel).** Модель содержит данные и логику приложения, представление - отображает данные пользователю, а модель представления связывает модель и представление и обрабатывает пользовательские действия.

Пример кода для **MVVM-подхода** с использованием **ViewModel и LiveData:**

**class MainViewModel : ViewModel() {**
**private val data = MutableLiveData<String>()**

**init {**
**// получение данных из модели и передача их в LiveData**
**data.value = Model.getData()**
**}**

**fun getData(): LiveData<String> {**
**return data**
**}**
**}**

**class MainActivity : AppCompatActivity() {**
**private lateinit var viewModel: MainViewModel**
**private lateinit var textView: TextView**
**override fun onCreate(savedInstanceState: Bundle?) {**
**super.onCreate(savedInstanceState)**
**setContentView(R.layout.activity_main)**
**textView = findViewById(R.id.textView)**
**viewModel = ViewModelProvider(this).get(MainViewModel::class.java)**
**viewModel.getData().observe(this, Observer<String> { data ->**
**textView.text = data**
**})**
**}**
**}**

---

**Dependency injection (DI)** - это подход, при котором зависимости (например, объекты) вводятся в класс извне, а не создаются внутри класса. Это позволяет легко изменять поведение класса и упрощает тестирование кода.

Пример: в классе **MainPresenter** для получения данных используется **ApiService.** Вместо создания объекта **ApiService** внутри **MainPresenter,** мы можем ввести его извне через конструктор или метод. Это называется внедрением зависимостей:

**kotlin:**

**class MainPresenter(private val apiService: ApiService) : MainContract.Presenter {**
**...**
**}**
   
---

**Hilt** - это фреймворк для реализации **DI** в приложениях на **Android.** Он облегчает конфигурирование и предоставление зависимостей с помощью аннотаций и генерации кода на этапе компиляции.

Пример: в классе **MainPresenter** для получения данных мы можем использовать **Hilt** для ввода **ApiService** в конструктор:

**kotlin:**

**class MainPresenter @Inject constructor(private val apiService: ApiService) : MainContract.Presenter {**
**...**
**}**
   
---

**Maps** - это инструмент для работы с картами в **Android-приложениях.** Он позволяет отображать карты, маркеры, маршруты и другие элементы на карте. Для работы с картами в **Android** используется **Google Maps API,** который предоставляет набор классов и методов для работы с картами.

Пример: для отображения карты на экране в приложении на **Kotlin** мы можем использовать **MapView:**

class MapActivity : AppCompatActivity() {
private lateinit var mapView: MapView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_map)

        mapView = findViewById(R.id.mapView)
        mapView.onCreate(savedInstanceState)

        mapView.getMapAsync { googleMap ->
            // Действия с картой
        }
    }

    override fun onResume() {
        super.onResume()
        mapView.onResume()
    }

    override fun onPause() {
        super.onPause()
        mapView.onPause()
    }

    override fun onDestroy() {
        super.onDestroy()
        mapView.onDestroy()
    }

    override fun onLowMemory() {
        super.onLowMemory()**
        mapView.onLowMemory()
    }
}

---
