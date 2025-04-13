# Ролевая модель и ее описание

**Легенда:**

Экспортер продукции агропромышленного комплекса, будь то юридическое лицо или индивидуальный предприниматель, заинтересован в расширении рынка сбыта и стремится продавать свою продукцию на рынках других стран. Для продвижения своей продукции он планирует использовать демонстрационно-дегустационные павильоны, расположенные за границей, которые посещают потенциальные импортеры в рамках различных мероприятий и выставок. Российский экспортный центр (РЭЦ) предлагает услуги по размещению и продвижению продукции на зарубежных рынках с целью популяризации товаров агропромышленного комплекса российского производства. В каждой стране павильоном управляет организация-оператор, имеющая договор с РЭЦ. Все расходы на размещение и продвижение продукции берет на себя РЭЦ, в то время как обязанностью экспортера является доставка продукции в павильон.

## Описание ролей

- **Экспортёр:**
    - **Сотрудник** — готовит проекты документов (заявки, отчёты и др.), вносит необходимые исправления и передаёт подготовленные материалы на подпись уполномоченному лицу
    - **Представитель с правом подписи** — руководитель организации или уполномоченный сотрудник (на основании доверенности) имеет право подписывать документы. Также в их компетенции — принятие решений о заявке на услугу или отказе от неё
- **РЭЦ:**
    - **Эксперт** — проверяет отчёты экспортёра и оператора, анализирует предоставленные планы и при необходимости формирует замечания. В его обязанности также входит консультирование представителей экспортёра и оператора по вопросам устранения выявленных недочётов.
    На завершающем этапе сотрудник готовит проект итогового отчёта об оказании услуги для последующего направления в Минсельхоз
    - **Уполномоченное лицо** — утверждает отчет экспортера и согласовывает план/отчет оператора павильона от имени РЭЦ. Также уполномочен подписывать годовой отчет перед его подачей в Минсельхоз
    - **Администратор** — задает сроки подачи заявок, подписания документов, сдачи отчетности и настраивает другие параметры системы
- **Оператор павильона:**
    - **Эксперт** — консультирует экспортёра при подписании соглашения, проверяет и корректирует данные о продукции перед публикацией на портале GoodFoodRussia. Принимает продукцию, оформляя соответствующий акт, а также составляет проекты планов и отчётов
    - **Уполномоченное лицо** — подписывает документы, подготовленные экспертом. Способ подписания зависит от статуса оператора: для российских организаций используется УКЭП, для иностранных — собственноручная подпись
- **Минсельхоз:**
    - **Эксперт** — проверяет планы и отчёты оператора павильона, а также годовой отчёт РЭЦ. При выявлении недочётов направляет документы на доработку с замечаниями. После проверки передаёт материалы на подпись уполномоченному сотруднику
    - **Уполномоченное лицо** — утверждает планы/отчёты оператора и РЭЦ после проверки экспертом

## Наследование полномочий

![Наследование полномочий](./img/inheritancePermissions.drawio.svg)

## ABAC-Политики
- Экспортёр может взаимодействовать с сущностями (заявка, соглашение, акт, отчёт) только своей компании;
- Оператор павильона может взаимодействовать с сущностями, которые созданы в рамках заявок в его павильон;
- Оператор являющийся резидентом РФ подписывает ПФ УКЭП;
- Оператор являющийся нерезидентом РФ загружает скан ПФ подписанной «живой» подписью.

## Матрица полномочий

<table>
    <div>
        <tr bgcolor="#f8f7f7">
            <th rowspan="2">Функция ↓ / Роль →</th>
            <th colspan="2">Экспортёр (Клиент)</th>
            <th colspan="3">РЭЦ</th>
            <th colspan="2">Оператор павильона</th>
            <th colspan="2">Минсельхоз</th>
        </tr>
        <tr bgcolor="#f8f7f7">
            <th>Сотрудник</th>
            <th>Представитель с правом подписи</th>
            <th>Эксперт</th>
            <th>Уполномоченное лицо</th>
            <th>Администратор сервиса</th>
            <th>Эксперт</th>
            <th>Уполномоченное лицо</th>
            <th>Эксперт</th>
            <th>Уполномоченное лицо</th>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Заявка</b></td>
        </tr>
        <tr>
            <td>Создать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать реквизиты</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Добавить продукцию</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Удалить продукцию</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи"> <b>+</b> </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отказаться от услуги</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи"> <b>+</b> </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Просмотреть ПФ</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Соглашение</b></td>
        </tr>
        <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать реквизиты</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Удалить продукцию</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи"> <b>+</b> </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Просмотреть ПФ</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Перенести срок доставки</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи"> <b>+</b> </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Сведения о продукции для GoodFoodRissia.com</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Загрузить фото</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Удалить фото</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отправить на проверку</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отклонить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Утвердить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Акт приёмки-передачи продукции</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи"> <b>+</b> </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  > <b>+</b> <br> (резидент РФ) </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Загрузить подписанную скан-копию</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >         </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">         </td>
            <td align="center" class="РЭЦ.Эксперт"                             >         </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >         </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >         </td>
            <td align="center" class="Оператор павильона.Эксперт"              >         </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  > <b>+</b> <br> (нерезидент РФ) </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >         </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >         </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Отчёт экспортёра</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи"> <b>+</b> </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     > <b>+</b> </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отклонить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Добавить комментарий</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Утвердить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 > <b>+</b> </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>План работ оператора</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  > <b>+</b> <br> (резидент РФ) </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Загрузить подписанную скан-копию</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  > <b>+</b> <br> (нерезидент РФ) </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Добавить комментарий</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отклонить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Согласовать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 > <b>+</b> </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Утвердить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          > <b>+</b> </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Отчёт оператора</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  > <b>+</b> <br> (резидент РФ) </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >         </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >         </td>
        </tr>
        <tr>
            <td>Загрузить подписанную скан-копию</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  > <b>+</b> <br> (нерезидент РФ) </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Добавить комментарий</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отклонить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Согласовать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 > <b>+</b> </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Утвердить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          > <b>+</b> </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Отчёт РЭЦ</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Подписать УКЭП</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 > <b>+</b> </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Выгрузить ПФ на локальный компьютер</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             > <b>+</b> </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Добавить комментарий</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Отклонить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      > <b>+</b> </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Утвердить</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               >          </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          > <b>+</b> </td>
        </tr>
    </div>
    <div>
        <tr bgcolor="#e1ffe7"> 
            <td colspan="12"><b>Настройки сервиса</b></td>
        </tr>
        <tr>
            <td>Просмотреть</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
        <tr>
            <td>Редактировать</td>
            <td align="center" class="Экспортёр.Сотрудник"                     >          </td>
            <td align="center" class="Экспортёр.Представитель с правом подписи">          </td>
            <td align="center" class="РЭЦ.Эксперт"                             >          </td>
            <td align="center" class="РЭЦ.Уполномоченное лицо"                 >          </td>
            <td align="center" class="РЭЦ.Администратор сервиса"               > <b>+</b> </td>
            <td align="center" class="Оператор павильона.Эксперт"              >          </td>
            <td align="center" class="Оператор павильона.Уполномоченное лицо"  >          </td>
            <td align="center" class="Минсельхоз.Эксперт"                      >          </td>
            <td align="center" class="Минсельхоз.Уполномоченное лицо"          >          </td>
        </tr>
    </div>
</table>