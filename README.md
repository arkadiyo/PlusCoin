# PlusCoin - cryptocurrency for the people

[![PlusCoin](https://pluscoin.io/images/dsp/pluscoin_alpha_cut.png)](https://pluscoin.io/images/dsp/pluscoin_alpha_cut.png)

**PlusCoin** - крипто-валюта, основа децентрализованной cashback платформы компании DSPlus. Инструмент для маркетинга оффлайн и онлайн организаций, привлечения новых игроков и потребителей в blockchain.

# Смарт-контракты

Смарт-контракт PlusCoin содержит:

  - Библиотеку "SafeMath" для защиты от переполнения во время математических
операций.

  - Стандартные функции и события ERC20 (Только владелец смарт-контракта может использовать эти функции на стадиях Presale и ICO 1-3):
    - `function balanceOf(address _owner) constant returns (uint256 balance) {}`
    Возвращает кол-во монет на балансе по указанному адресу;
    - `function transfer(address _to, uint256 _value) returns (bool success) {}`   
    Отправляет монеты по указанному адресу (с баланса отправителя);
    - `function transferFrom(address _from, address _to, uint256 _value) returns (bool success) {}`
    Отправляет монеты с указанного адреса на указанный адрес, если владелец адреса списания разрешил данную операцию.
    - `function approve(address _spender, uint256 _value) returns (bool success) {}`
    Разрешает списание указанного количества монет указанному адресу со счета отправителя сообщения
    - `function allowance(address _owner, address _spender) constant returns (uint256 remaining) {}` 
    Возвращает общее количество монет, разрешенных для списания с указанного адреса, другим адресом.

  - Публичные переменные и константы:
    - `name` – название токена;
    - `symbol` – символ токена;
    - `decimals` – кол-во единиц после запятой у криптовалюты;
    - `totalSupply` – общее количество монет;
    - `PRESALE_PRICE` – стоимость за 1 эфир;
    - `current_state` – текущее состояние контракта;
    - `OWNER_MIN_LIMIT` – минимальное кол-во монет;
    - `TOKEN_PRESALE_LIMIT` – лимит монет для продажи на стадии Presale;
    - `TOKEN_ICO1_LIMIT` – лимит монет для продажи на стадии ICO 1;
    - `TOKEN_ICO2_LIMIT` - лимит монет для продажи на стадии ICO 2;
    - `TOKEN_ICO3_LIMIT` - лимит монет для продажи на стадии ICO 3.

  - Функции для стадий Presale и ICO и др.:
    - `function transferOwnership(address newOwner) onlyOwner {}`
    Позволяет владельцу контракта передавать владение другому адресу;
    - `function buy() public payable {}`
    Функция для покупки монет у владельца контракта в автоматическом режиме, активна только на стадии Presale и ICO 1-3;
    - `function buyTokens(address _buyer) public payable {}
    Функция для покупки монет с зачислением на указанный адрес;
    - `function get_token_state() public constant returns (State) {}`
    Получить текущий статус контракта;
    - `function setTokenState(State _nextState) public onlyOwner`
    Изменить статус контракта;
    - `function remaining_for_sale() public constant returns (uint remaining_coins)`
    Возвращает оставшееся кол-во монет на продажу в текущей стадии в соответствии с установленными лимитами.
    
Доступные статусы контракта: Создан, Presale, ICO1, ICO2, ICO3, Свободная торговля, Пауза. 
Статусы возможно изменить только в одном направлении
(от «Создан» до «Свободная торговля»). Однако, владелец смарт-контракта может
приостановить продажу на стадии Presale, переведя контракт в состояние "Пауза". Это
необходимо для защиты от непредвиденных ситуаций. Переход в стадию Пауза и
обратно возможно только из стадий Presale или ICO.

Основной смарт-контракт, в соответствии со стандартом ERC20, обеспечивает базовые функции для держателей PlusCoin:
  - возможность проверки балансов по адресу кошелька;
  - возможность, для владельца кошелька, отправить PLC на любой другой кошелек;
  - возможность, для владельца кошелька, разрешить определенную сумму для списания в пользу другого адреса (allowance);
  - возможность списать средства с указанного кошелька, с разрешения его владельца.

Поддержка этих функций позволяет использовать PlusCoin как стандартную криптовалюту на базе сети Etherium (в том числе, размещение на биржах и обменных сервисах).

# Дополнительные контракты

Мы не собираемся ограничиваться только стандартным функционалом ERC20, поэтому ведем активную разработку дополнительных смарт-контрактов, которые будут взаимодействовать с основным. Эти контракты обеспечат функционирование сервиса DSPlus в blockchain-сети. Публикация дополнительных смарт-контрактов не затронет работу основного и НЕ будет сопровождаться выпуском новых "монет" вместо PlusCoin. Дополнительные смарт-контракты лишь обеспечат корректное взаимодействие функционала сервиса DSPlus и основного контракта PlusCoin.

Комманда DSPlus видит большие перспективы и возможности, которые открывает широкое использование blockchain-технологий в реальном мире. Использование смарт-контрактов в бизнес-процессах компаний, государственной и социальной сфере необратимо. Это вопрос времени. Поэтому мы постоянно ведем мониторинг новейших разработок в области смарт-контрактов, изучая возможности их применения. А так же готовим собственные контракты, которые в самое ближайшиее время обеспечат:
  - проведение безопасных и прозрачных сделок в компаниях-партнерах DSPlus, а так же нашем интернет-магазине;
  - проведение безопасных и прозрачных сделок на P2P-площадке приложения DSPlus (сделки с арбитром и без);
  - введение понятия цифровой собственности, которая переходит от одного владельца к другому в результате совершения сделки;
  - введение "криптоскоринга" (рейтинга) для держателей PlusCoin, на основе которого могут приниматься, например, решения в пользу кредитования того или иного держателя PlusCoin;
  - обеспечение безопасных сделок по кредитованию в PlusCoin (в т.ч. p2p кредитование).

В настоящий момент мы проводим тестирование контракта для сделок, содержащего первые функции крипто-скорринга. Код данного контракта будет опубликован в данном репозитории в самое ближайшее время, после проведения тестирования и внешнего аудита.

Кроме этого, мы не ограничиваемся перечисленными выше функциями и постоянно обсуждаем и прорабатываем новые идеи для внедрения blockchain-технологий в реальную жизнь.

### Дополнительные материалы
Вы можете получить дополнительную информацию о проекте на наших официальных ресурсов:
* [Facebook] - official group on FB
* [Telegram] - official Telegram-channel
* [Pluscoin.io] - official PlusCoin web-site
* [Youtube] - official youtube channel

По всем вопросам Вы можете написать нам по адресу mail@dsplus.pro
Спасибо за Ваше внимание к проекту!.

[//]: #

   [Facebook]: <https://www.facebook.com/dsplus.fork?fref=ts>
   [Telegram]: <https://t.me/joinchat/C9pDig06uYbTgoEq6N4ShQ>
   [Pluscoin.io]: <http://pluscoin.io>
   [Youtube]: <https://www.youtube.com/channel/UCeniN6CmMqp_ujbkWtSmaEA>
